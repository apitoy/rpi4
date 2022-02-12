[Getting started with Camel K tutorial - Masterspringboot -](http://www.masterspringboot.com/camel/getting-started-with-camel-k-tutorial/)

+ [DOCKER.md](DOCKER.md)


## MINIKUBE config

    minikube config set driver docker
    


## MINIKUBE start

    minikube start --driver=docker


## After the startup process is completed, you need to enable the registry addon:

    minikube addons enable registry

## Alternatively, you can also start an instance with the registry addon in one command:

    minikube start --addons registry


 
 
 

## Build kamel

    kamel install
    
 OR use the --force option to overwrite existing resources


    kamel install --force
    
# When the installation is completed, you should be to see the camel-k operator in your Kubernetes pods:   

    minikube kubectl get pods


## Prepare script

file

    nano hello.groovy 

content

    from("timer:tick?period=3s")   
    .setBody().constant("Hello from Camel K in Groovy!!!")   
     .to("log:message")
     
run kamel

    kamel run hello.groovy

run with logs

    kamel run hello.groovy --dev 

