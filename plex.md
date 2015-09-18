# Installing Plex on Fedora

Plex is a media management/streaming application that allows you to access your home media collection from anywhere. It has two main components: Plex Media Server (the software that you should run on your home server that has all your media files) and Plex Home Theater (the software you should run on any computer you want to access your media from).

## Plex Media Server

Plex Media Server actually directly supports lots of Linux distros, including Fedora. Just [use the RPM from their site](http://plex.tv/downloads).

## Plex Home Theater

Plex does not offer official support for Linux for the home theater application. Fortunately, it's open source and community builds are available.

Theoretically, there are supposed to be Plex Home Theater builds offered by a Plex staff member on [this forum post](https://forums.plex.tv/discussion/comment/505575/). However, it's out of date -- the only links are for Fedora 20 and Fedora 21. The Fedora 21 repo is completely empty and the Fedora 20 repo purportedly doesn't work with Fedora 21+.

Fortunately, a community member has put up a repo for Fedora 21 and 22 in [this forum post](https://forums.plex.tv/discussion/154814/plex-home-theater-rpm-for-fedora). Follow the instructions there to install it. You could also build it from source if you want ([here's the Git repo](http://github.com/plexinc/plex-home-theater-public)), but the build process is poorly documented and kind of a pain in the butt.
