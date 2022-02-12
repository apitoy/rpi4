# rpi4 / DOCKER
Install system and software 

+ [minikube ubuntu](minikube-ubuntu.md)
+ [minikube raspbian](minikube-raspbian64.md)

CPU arm64v8

## we need to change this file again to enable CGroup. Kubernetes requires CGroup to provide proper resource limits control and management. You can refer to this site for a better explanation of CGroup.

    sudo echo "/ncgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1/n" >> /boot/cmdline.txt

OR

sudo nano /boot/cmdline.txt
group_enable=cpuset cgroup_enable=memory cgroup_memory=1



# docker / ubuntu

## update

    sudo apt-get update -y && sudo apt-get upgrade -y
    
## install docker on ubuntu
[Install Docker Engine on Ubuntu | Docker Documentation](https://docs.docker.com/engine/install/ubuntu/)

update system

    sudo apt-get update

install dependencies

    sudo apt-get install ca-certificates curl gnupg lsb-release

Add Docker’s official GPG key:

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

set up the stable repository.

    echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

install

    sudo apt-get update
    sudo apt-get install -y docker-ce docker-ce-cli containerd.io

## install docker

32 bit (armhf)

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=armhf] https://download.docker.com/linux/ubuntu bionic stable"
    sudo apt-get update
    
    sudo apt-get install -y docker
    sudo apt-get install docker-ce-cli:armhf

OR

https://mrbradleylee.com/posts/01/2022/installing-docker-on-an-rpi-4/


    sudo apt install linux-modules-extra-raspi
    
OR

    sudo apt install -y docker.io
    
 
OR

    sudo snap install docker

## uninstall

    sudo apt-get purge docker-engine

## restart

    sudo service docker restart
    
## user and group 

    sudo groupadd docker

    sudo usermod -aG docker $USER


Run the following command or Logout and login again and run (that doesn't work you may need to reboot your machine first)

    newgrp docker


rights

    sudo chmod 666 /var/run/docker.sock

check

    docker version



## run

    docker run hello-world

# DOCKER / images

    docker run hello-world
    docker images

remove all

    docker rmi -f $(docker images -aq)
 
all from cache

    docker builder prune -af
    

# DOCEKR / network


    docker network ls
    docker network rm [id]
    docker network prune
    

# Net Tools

    sudo apt-get install hostpad
    sudo apt-get install bind9
    sudo apt-get install isc-dhcp-server
    sudo apt-get install iw
    sudo apt-get install monit
    sudo apt-get install dos2unix
    sudo apt-get install telnet
    sudo apt-get install ethtool
  
