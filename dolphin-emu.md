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

I kinda went overboard here; you probably don't need most of the non-devel versions of anything that has a devel equivalent (mea culpa).
