
# minikube / DEBIAN

+ [DOCKER.md](DOCKER.md)


check architecture

    sudo dpkg --print-architecture

## Edit cmdline

    sudo nano /boot/cmdline.txt

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


    sudo apt-get update
    
    sudo apt install -y docker.io

    sudo usermod -aG docker $USER && newgrp docker

    docker run --rm hello-world

[Install kubectl on Raspberry Pi using the Snap Store | Snapcraft](https://snapcraft.io/install/kubectl/raspbian)

    sudo apt update
    sudo apt install -y snapd
    sudo reboot
    sudo snap install core
    sudo snap install kubectl --classic


## DOCKER

systemctl restart docker
docker network prune

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
    
    
