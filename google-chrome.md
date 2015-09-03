# Easily install Chrome on Fedora 22

Getting Chrome should be one of the easiest tasks ever, but it's not. This document aims to fix that

## Installing Chrome

If you have [Fedy](https://satya164.github.io/fedy/) installed, you can use it to install Chrome. If you don't have Fedy, you can just paste this into your terminal (you don't need root):

```
cat << EOF | sudo tee /etc/yum.repos.d/google-chrome.repo
[google-chrome]
name=google-chrome - \$basearch
baseurl=http://dl.google.com/linux/chrome/rpm/stable/\$basearch
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub
EOF
sudo yum -y install google-chrome-stable
```

This command adds the official Google Chrome repository to your Yum repository list, and then installs Chrome with Yum.

## Fixing two icons

Chrome's official Fedora releases have a bug in them that causes Chrome to appear twice in your dock. You'll have "Google Chrome" in your favorites, but when you click it, it'll launch as a separate icon labeled "Google-chrome-stable". Here's a really simple command that can fix this (you may also need to re-run this after updating Chrome):

```
sudo sed -i.bak '/\[Desktop Entry\]/a StartupWMClass=Google-chrome-stable' /usr/share/applications/google-chrome.desktop
```

GNOME may take a little while to notice that you've done this. If you want to make GNOME update immediately, press Alt+F2, type "r", and press enter; this will make GNOME reset itself.
