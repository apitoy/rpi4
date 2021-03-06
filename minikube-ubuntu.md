
# minikube / UBUNTU

+ [DOCKER.md](DOCKER.md)
[Installing Camel-K on microk8s running Ubuntu - Aymen Furter - Medium](https://aymen-furter.medium.com/installing-camel-k-on-microk8s-running-ubuntu-5e286d057623)

[Setup Minikube on RPi4 4GB — Ubuntu Server 20.04 LTS | by Akash Kumar | Medium](https://medium.com/@Aakash1sky/setup-minikube-on-rpi4-4gb-ubuntu-server-20-04-lts-a4a852f54354)

check architecture

    sudo dpkg --print-architecture

## Edit cmdline

    sudo nano /boot/firmware/cmdline.txt

## Append to cmdline.txt

    cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1

## restart

    sudo reboot

## verify the cmdline changes 

    cat /proc/cmdline


## install tools

    sudo apt install -y net-tools
    sudo apt install -y git openssh-server

## Install Docker - Minikube DRIVER


[Installing Docker in Raspberry Pi 4](https://brjapon.medium.com/setting-up-ubuntu-20-04-arm-64-under-raspberry-pi-4-970654d12696)

    sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    sudo add-apt-repository "deb [arch=arm64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"


    sudo apt-get update

    apt-cache policy docker-ce

    sudo apt-get -y install docker-ce

    sudo usermod -aG docker $USER && newgrp docker

    docker run --rm hello-world

[Install kubectl on Raspberry Pi using the Snap Store | Snapcraft](https://snapcraft.io/install/kubectl/raspbian)

    sudo apt update
    sudo apt install snapd
    sudo reboot
    sudo snap install core
    sudo snap install kubectl --classic



## docs

https://braindose.blog/2021/12/31/install-kubernetes-raspberry-pi/#disable-ubuntu-swap
https://braindose.blog/2021/12/28/kubernetes-raspberry-pi-ubuntu/

https://medium.com/@Aakash1sky/setup-minikube-on-rpi4-4gb-ubuntu-server-20-04-lts-a4a852f54354

## ENV

### Disable Ubuntu Swap

You need to disable the Ubuntu swap in order for the “kubelet” to run properly. You just need to run the following command to turn the swap off.

    sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
    sudo swapoff -a


[minikube start | minikube](https://minikube.sigs.k8s.io/docs/start/)


    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm
    sudo install minikube-linux-arm /usr/local/bin/minikube



# minikube / RASPBIAN
  
  
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm
    sudo install minikube-linux-arm /usr/local/bin/minikube  

    kubeadm config images pull
  

## MINIKUBE config

    minikube config set driver docker
    minikube start --driver=docker



## MINIKUBE start

    minikube start
    minikube logs --file=logs.txt
    systemctl enable kubelet.service
 
# Low memory

https://github.com/kubernetes/minikube/issues/6843

    sudo minikube start --vm-driver=none

    sudo minikube start --memory 2048 --cpus 2

    free -m
    tail -5 /etc/dphys-swapfile

    dockerd --storage-opt dm.basesize=20G
    
    
