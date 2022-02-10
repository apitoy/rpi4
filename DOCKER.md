# rpi4 / DOCKER
Install system and software 

+ arm64v8


# docker / ubuntu

    sudo apt-get update && sudo apt-get upgrade

    sudo apt install docker.io

OR

    sudo snap install docker

    sudo groupadd docker

    sudo usermod -aG docker $USER


    #Run the following command or Logout and login again and run (that doesn't work you may need to reboot your machine first)

    newgrp docker


    sudo chmod 666 /var/run/docker.sock

    docker version



## run

    docker run hello-world


# minikube / UBUNTU

[minikube start | minikube](https://minikube.sigs.k8s.io/docs/start/)


    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm
    sudo install minikube-linux-arm /usr/local/bin/minikube



# minikube / RASPBIAN
  
  
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-arm
    sudo install minikube-linux-arm /usr/local/bin/minikube  

    kubeadm config images pull
  

## MINIKUBE config

    minikube start --driver=docker
    minikube config set driver docker


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
  
