
# minikube / DEBIAN / raspbian 64 bit

+ [DOCKER.md](DOCKER.md)


check architecture

    sudo dpkg --print-architecture

## Edit cmdline

    sudo nano /boot/cmdline.txt

## Append to cmdline.txt on the end of first line

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

### rights

    sudo usermod -aG docker $USER && newgrp docker

### Run image

    docker run --rm hello-world

### restart

    systemctl restart docker
 
### remove
    docker network prune



[Install kubectl on Raspberry Pi using the Snap Store | Snapcraft](https://snapcraft.io/install/kubectl/raspbian)

    sudo apt update
    sudo apt install -y snapd
    
restart

    sudo reboot
    
install

    sudo snap install core
    sudo snap install kubectl --classic



## docs

https://braindose.blog/2021/12/31/install-kubernetes-raspberry-pi/#disable-ubuntu-swap
https://braindose.blog/2021/12/28/kubernetes-raspberry-pi-ubuntu/

https://medium.com/@Aakash1sky/setup-minikube-on-rpi4-4gb-ubuntu-server-20-04-lts-a4a852f54354

## ENV


[minikube start | minikube](https://minikube.sigs.k8s.io/docs/start/)

# minikube / RASPBIAN
  
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm64

    sudo install minikube-linux-arm64 /usr/local/bin/minikube
  

## MINIKUBE config

    minikube config set driver docker
    


## MINIKUBE start

    minikube start --driver=docker

OR

    minikube start

LOGS
    
    minikube logs --file=logs.txt
    systemctl enable kubelet.service
 
## Snapd

    sudo apt update
    sudo apt install snapd
    sudo reboot
`

## Kubectl install


[Install kubectl on Raspberry Pi using the Snap Store | Snapcraft](https://snapcraft.io/install/kubectl/raspbian)


    sudo snap install core
    sudo snap install kubectl --classic

 
# Low memory

https://github.com/kubernetes/minikube/issues/6843

    sudo minikube start --vm-driver=none

    sudo minikube start --memory 2048 --cpus 2

    free -m
    tail -5 /etc/dphys-swapfile

    dockerd --storage-opt dm.basesize=20G
    
    


## Install go

    sudo apt update 
    sudo apt install -y golang
    export GO111MODULE=off
    go env

## Install Java

    sudo apt update
    sudo apt install default-jdk
    java -version

    sudo apt install openjdk-8-jdk



## Build kamel

    git clone https://github.com/apache/camel-k.git
    make clean
    make
    cp kamel /usr/local/bin/kamel
    make images
    env GOOS=linux GOARCH=amd64 make build-kamel
    cp kamel build/_output/bin/
    operator-sdk build docker.io/apache/camel-k:1.0.0-M2-SNAPSHOT
    kamel install




https://github.com/apache/camel-k/releases/tag/v1.8.0

curl https://github.com/apache/camel-k/releases/download/v1.8.0/camel-k-client-1.8.0-linux-64bit.tar.gz
		
tar -xf camel-k*tar.gz
scp kamel pi@rpilite:/home/pi


kamel install
ps -ef | grep kube



nano helloworld.groovy 

