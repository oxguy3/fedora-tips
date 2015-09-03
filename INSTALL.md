# After you install Fedora

So you've just done a clean install of Fedora 22. Let's get started making your OS more homey (most of these steps are optional and up to your discretion).

## Take control of root

If you haven't already set a root password, you're probably going to need it for at least a couple things. Change it using `sudo passwd`. This is the most critical password on your machine (and not something you'll need to use very often), so make it pretty strong and secure.

## Add RPMFusion repositories

Fedora's official repositories let you install a lot with YUM, but they're also missing a lot. RPMFusion is the crucial third-party source for all the stuff the official repos are missing. This command will install both RPMFusion repos (free and non-free) for your version of Fedora:

```
su -c 'yum install --nogpgcheck http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm'
```

## Update everything

Odds are, whatever release you installed was already outdated from the moment you installed it. Run this to bring your system up to speed:

```
sudo yum update
```

## Install Fedy

Fedy is a tool for installing lots of little bits of useful software that aren't necessarily available via easier means. Use it to install Chrome, Steam, Skype, Java, Adobe Flash, text editors, IDEs, and other software and tweaks. Here's the command:

```
bash -c 'su -c "curl https://satya164.github.io/fedy/fedy-installer -o fedy-installer && chmod +x fedy-installer && ./fedy-installer"'
```

Fedy is a GUI application, and thus can be launched from the application list.

## Install Google Chrome

If you don't like Firefox, you probably want Chrome. You can just open Fedy to install Chrome, or you can use [this guide](https://github.com/oxguy3/fedora-scratch/blob/master/google-chrome.md). Even if you do use Fedy, you might want to check out that guide, as it has a fix for an issue where Chrome has two separate icons on your dock.

## Install Tweak Tool

GNOME Tweak Tool is pretty quintessential for changing appearance and behavior of GNOME (your desktop manager).

```
sudo yum install gnome-tweak-tool
```

Once installed, Tweak Tool will appear in the Utilities section of your application list. The whole app is worth exploring if you're a power user. A few particularly neat tweaks I like that Tweak Tool offers:

* Appearance>Global Dark Theme: makes most applications dark themed
* Windows>Titlebar Buttons: options to add Minimize and Maximize buttons to all windows

## Improve the font rendering

Text looks really ugly by default on Fedora. There's a couple things you can do about this. First install FreeType:

```
sudo yum install freetype
```

Next, open Fedy. From the Apps tab, install Microsoft TrueType core fonts. From the Tweaks tab, enable Better font rendering.

Lastly, open Tweak Tool. Go to the Fonts section and set Hinting to "Slight" and Antialiasing to "Rgba".

## Install propreitary graphics drivers

Fedora ships with a set of free graphics drivers called Nouveau. They get the job done, but if you want to play games or otherwise utilize a powerful graphics card, you'll want to get the drivers from your GPU's manufacturer. For my NVIDIA drivers, [this tutorial was a godsend](https://kaischroed.wordpress.com/howto-install-nvidia-driver-on-fedora-replacing-nouveau/) ([archived version if link goes down](https://archive.is/M2deU)).

## Video software

For watching any sort of video content, you'll probably want to install VLC:

```
sudo yum install vlc
```

You also may want to use Fedy to install Multimedia codecs to support lots of file types.

## Other applications

Here are a couple easy-to-install applications you might want:

* GIMP: powerful photo-editing software (good replacement for Adobe Photoshop): `sudo yum install gimp`
* Inkscape: vector image editing software (good replacement for Adobe Illustrator): `sudo yum install inkscape` 
* Wine: allows you to run Windows-only applications on Linux: `sudo yum install wine`
* YumEx: a graphical interface for Yum (nice if you aren't comfortable on the command line): `sudo yum install yumex`
