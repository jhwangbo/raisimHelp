# raisimHelp (For debian distributions)

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
From ([3](https://tecadmin.net/install-ffmpeg-on-linux/)).
```
sudo add-apt-repository ppa:jonathonf/ffmpeg-4
sudo apt-get update
sudo apt-get install ffmpeg
```

## virtualenv
From ([4](https://medium.com/@aaditya.chhabra/virtualenv-with-virtualenvwrapper-on-ubuntu-34850ab9e765)).
### setup
```
sudo apt-get install python-pip
sudo pip install virtualenv virtualenvwrapper
```
add the following lines to .bashrc
```
export WORKON_HOME=~/.virtualenvs
/usr/local/bin/virtualenvwrapper.sh
```

### make a new virtualenv
```
mkvirtualenv MYPROJECT_NAME
```
## Add SSH key
From ([5](https://confluence.atlassian.com/bitbucket/set-up-an-ssh-key-728138079.html))
```
ssh-keygen
```
Set them all default

```
cat ~/.ssh/id_rsa.pub
```

## Install docker && Nvidia-docker2
### docker
From ([6](https://docs.docker.com/install/linux/docker-ce/debian/))
uninstall older versions
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```
 
 install
 ```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
 ```
 
### nvidia-docker2
From ([7](https://github.com/NVIDIA/nvidia-docker))

```
# If you have nvidia-docker 1.0 installed: we need to remove it and all existing GPU containers
docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge -y nvidia-docker

# Add the package repositories
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update

# Install nvidia-docker2 and reload the Docker daemon configuration
sudo apt-get install -y nvidia-docker2
sudo pkill -SIGHUP dockerd

# Test nvidia-smi with the latest official CUDA image
docker run --runtime=nvidia --rm nvidia/cuda:9.0-base nvidia-smi
```
