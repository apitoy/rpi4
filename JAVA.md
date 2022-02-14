## Install Java

update

    sudo apt update
    sudo apt install default-jdk
    java -version

install

    sudo apt install openjdk-8-jdk

    sudo apt install -y maven

start projects 

    cd IdeaProjects/camel-spring-boot-examples


    java -jar camel-example-spring-boot-rest-openapi-3.16.0-SNAPSHOT.jar



## Many sh with java

This should do it.

    #!/bin/bash
    
    files="$@"
    
    for i in $files;
    do
        echo "Doing $i"
        java -jar javaapp.jar <<< "$i"
    done
    

Make sure you can execute

    chmod u+x filename


call it like this:

    ./filename firstfile secondfile thirdfile etc.



# One sh java 

create a new text file and name it `hello.sh`


    !/bin/bash
    clear
    java -jar HelloWorld.jar
    

Save it and open terminal:

- navigate to directory where your `HelloWorld.jar` is present

- give permission to terminal to run the bash script by using the following command


        sudo chmod 754 hello.sh
    

- run you script by running the following command

        ./hello.sh
