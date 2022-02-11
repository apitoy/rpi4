# rpi4 / DOCKER
Install system and software 

+ [minikube.md](minikube.md)

+ arm64v8

## we need to change this file again to enable CGroup. Kubernetes requires CGroup to provide proper resource limits control and management. You can refer to this site for a better explanation of CGroup.

    sudo echo "/ncgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1/n" >> /boot/cmdline.txt

OR

sudo nano /boot/cmdline.txt
group_enable=cpuset cgroup_enable=memory cgroup_memory=1



# docker / ubuntu

update

    sudo apt-get update -y && sudo apt-get upgrade -y

install docker

    sudo apt install -y docker.io

OR

    sudo snap install docker

user and group 

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


# Net Tools

    sudo apt-get install hostpad
    sudo apt-get install bind9
    sudo apt-get install isc-dhcp-server
    sudo apt-get install iw
    sudo apt-get install monit
    sudo apt-get install dos2unix
    sudo apt-get install telnet
    sudo apt-get install ethtool
  
