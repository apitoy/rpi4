
# minikube / UBUNTU

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
    
    
