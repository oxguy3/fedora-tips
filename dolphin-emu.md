# Build Dolphin Emulator on Fedora

Dolphin Emulator is a really great emulator for GameCube and Wii games, but they only distribute official builds for Windows, OS X, and Ubuntu. To get it running on Fedora, you'll have to download the source code and build it yourself.

This guide was written based on [the official readme](https://github.com/dolphin-emu/dolphin/blob/master/Readme.md#building-for-linux-and-os-x) (as well as [the official wiki page on building Dolphin](https://wiki.dolphin-emu.org/index.php?title=Building_Dolphin_on_Linux)) and tested on Dolphin 5.0-rc-25. It may become outdated in time, but will probably remain generally accurate (the dependencies list will probably become outdated gradually, for example, but you should be able to get at least _most_ of them this way).

## Get the dependencies

Here are all the dependencies I found I needed. You can actually remove the non-devel versions of pretty much anything that has a "devel" version.

```
sudo yum -y groupinstall "Development Tools"
sudo yum -y install git cmake cmake-fedora gcc gcc-c++ alsa-lib-devel libao-devel \
bluez bluez-libs-devel pulseaudio-libs-devel openal-soft-devel ffmpeg-devel \
portaudio-devel libevdev-devel systemd-devel zlib-devel lzo-devel libpng-devel \
soundtouch-devel libusbx-devel SFML-devel polarssl-devel SOIL-devel \
miniupnpc-devel wxGTK-devel gtk2-devel
```

## Download the source code

Now you need to download all the source code for Dolphin. The first step is to locally clone their Git repository. `cd` to somewhere nice like your Documents folder, then do this:

```
git clone https://github.com/dolphin-emu/dolphin.git dolphin-emu
```

This will get the very latest code, which will probably be a bit unstable. I'd recommend using the code from a Release Candidate instead. To do this, find the release candidate (or dev version) you want on [Dolphin's site](https://dolphin-emu.org/download/). Click on the version number, and find a string of nonsense characters labeled "Commit" (this is called the commit hash). For example, I used [5.0-rc-25](https://dolphin-emu.org/download/dev/4f0e2f6b62655d197b89f693fc40464f9d2e75d3/), and my commit hash was "4f0e2f6b62655d197b89f693fc40464f9d2e75d3". Once you have the commit hash, run these commands:

```
cd dolphin-emu
git checkout yourCommithash .
```

This will rollback your local copy of the code to the release you selected.

## Build the application

Now you need to compile the code into a build.

```
mkdir Build
cd Build
cmake ..
make
sudo make install
```

Be sure there are no glaring error messages between each of those steps (warnings are fine, but fails and severe messages are not). Once you've run all that, Dolphin should be installed and you can find it in your application list. Enjoy your old games! :)
