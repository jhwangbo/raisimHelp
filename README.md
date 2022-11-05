# raisimHelp (For debian distributions)

## Basic tools that I use
sudo apt install git terminator libeigen3-dev doxygen mercurial valgrind liburdfdom-dev curl minizip ffmpeg && sudo snap install clion --classic && sudo snap install rider --classic

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

## How to use variables defined in your bashrc in clion
You have to modify your clion.desktop file. If you install normally, it should be located in 
```/home/YOUR_ID/.local/share/applications/jetbrains-clion.desktop ```

edit the line starting with ```Exec=``` to ```Exec=bash /WHERE/YOU/DOWNLOADED/CLION/bin/clion.sh```

This ensures that system variables (like LD_LIBRARY_PATH) are visible in clion.

# how to install gtest
From ([8](https://www.eriksmistad.no/getting-started-with-google-test-on-ubuntu/))

```
sudo apt-get install libgtest-dev
sudo apt-get install cmake # install cmake
cd /usr/src/gtest
sudo cmake CMakeLists.txt
sudo make
sudo cp *.a /usr/lib
```
