# Easily install Google Chrome on Fedora

Getting Chrome should be one of the easiest tasks ever, but it's not. This document aims to fix that.

## Installing Chrome

If you have [Fedy](https://satya164.github.io/fedy/) installed, you can just open it, find Google Chrome, and click Install. If you don't have Fedy, you can just paste this into your terminal (you don't need root):

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

## Fixing the 'double icons' issue

Chrome's official releases for many Linux distros, including Fedora, have a bug in them that causes Chrome to appear twice in your dock. You'll have "Google Chrome" in your favorites, but when you click it, it'll launch as a separate icon labeled "Google-chrome-stable". Here's a really simple command that can fix this:

```
sudo sed -i.bak '/\[Desktop Entry\]/a StartupWMClass=Google-chrome-stable' /usr/share/applications/google-chrome.desktop
```

GNOME may take a little while to notice that you've done this. If you want to make GNOME update immediately, press Alt+F2, type "r", and press enter; this will make GNOME reset itself. You might also need to re-run this command after any time you update Chrome.

### How this works

GNOME (which is your desktop environment software) uses `.desktop` config files to specify how applications in your dock and application list should look and act. If you have an app that launches itself with a different name than GNOME expects it to, GNOME won't realize it's actually the same app. This command adds a property to the `google-chrome.desktop` file that says "hey, 'Google-chrome-stable' is actually just the name that 'Google Chrome' launches itself as. they're the same thing!".

The command also saves the original `google-chrome.desktop` file as `google-chrome.desktop.bak`, in case for some reason you want to revert.
