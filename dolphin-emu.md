# Dolphin Emulator dependencies on Fedora
So you want to build Dolphin emulator on Fedora huh? Here's a big
ole command. There are build instructions [here](https://github.com/dolphin-emu/dolphin/blob/master/Readme.md#building-for-linux-and-os-x).

That link doesn't detail all the dependencies you'll need. Here's the
list I built up:

```
sudo yum -y groupinstall "Development Tools"
sudo yum -y install \
cmake cmake-fedora \
gcc gcc-c++ \
alsa-lib alsa-lib-devel \
libao libao-devel \
bluez bluez-libs-devel \
pulseaudio pulseaudio-libs-devel \
openal openal-soft-devel \
ffmpeg ffmpeg-devel \
portaudio portaudio-devel \
libevdev libevdev-devel \
systemd-devel \
zlib zlib-devel \
lzo lzo-devel \
libpng libpng-devel \
soundtouch soundtouch-devel \
libusbx libusbx-devel \
SFML SFML-devel \
polarssl polarssl-devel \
SOIL SOIL-devel \
miniupnpc miniupnpc-devel \
wxGTK wxGTK-devel \
gtk2 gtk2-devel
```

A lot of these are optional, but unless you're strapped for space, it's
probably best to build the most complete version of Dolphin possible. You
also probably have a lot of these; I was pretty thorough in some cases.
You may also need to have the RPMFusion repositories on your system to
get some of these.
