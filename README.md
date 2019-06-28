# raisimHelp

## How to install cmake?
From ([1](https://askubuntu.com/questions/355565/how-do-i-install-the-latest-version-of-cmake-from-the-command-line/865294)).

Raisim is using cmake>3.10. You can install it from source as
```commandline
version=3.14
build=5
mkdir ~/temp
cd ~/temp
wget https://cmake.org/files/v$version/cmake-$version.$build.tar.gz
tar -xzvf cmake-$version.$build.tar.gz
cd cmake-$version.$build/
./bootstrap
make -j4
sudo make install
```

check if it is properly installed by
```
cmake --version
```

## How to install latest version of g++?
From ([2](https://gist.github.com/jlblancoc/99521194aba975286c80f93e47966dc5)).

```commandline
sudo apt-get install -y software-properties-common
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt update
sudo apt install g++-8 gcc-8 -y
```

## How to install ffmpeg?
From ([3](https://tecadmin.net/install-ffmpeg-on-linux/))
```
sudo add-apt-repository ppa:jonathonf/ffmpeg-4
sudo apt-get update
sudo apt-get install ffmpeg
```
