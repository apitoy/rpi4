[Getting started with Camel K tutorial - Masterspringboot -](http://www.masterspringboot.com/camel/getting-started-with-camel-k-tutorial/)


## MINIKUBE config

    minikube config set driver docker
    


## MINIKUBE start

    minikube start --driver=docker


## deploy the registry.

    minikube addons enable registry 

LOGS
    
    minikube logs --file=logs.txt
    systemctl enable kubelet.service
 
 
 

## Build kamel

    kamel install
    
 OR use the --force option to overwrite existing resources


    kamel install --force
    
# When the installation is completed, you should be to see the camel-k operator in your Kubernetes pods:   

    minikube kubectl get pods


## Prepare script

file

    nano helloworld.groovy 

content

    from("timer:tick?period=3s")   
    .setBody().constant("Hello from Camel K in Groovy!!!")   
     .to("log:message")
     
run kamel

    kamel run hello.groovy

run with logs

    kamel run hello.groovy --dev 

