# EmulationStation dependencies on Fedora

EmulationStation has [very thorough documentation](https://github.com/Aloshi/EmulationStation/blob/master/README.md) for building on just about every OS... except Fedora. The general purpose Linux instructions mostly work, but the apt-get command for dependencies obviously won't fly. Here's the dependencies that I found I needed:

```
sudo yum -y groupinstall "Development Tools"
sudo yum -y install \
cmake cmake-fedora \
gcc gcc-c++ \
freeimage-devel \
SDL2-devel \
boost-devel \
eigen3-devel \
libcurl-devel
```
