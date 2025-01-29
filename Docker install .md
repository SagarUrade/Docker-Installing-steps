### DevOps Classroom notes 28/Jan/2025

## Installing docker on Ubuntu Linux

- Lets create an ec2 instance / azure  vm.

- ssh into it.

- execute the following commands to get the latest version of  docker .

 curl -fsSL https://get.docker.com -o install-docker.sh
 sudo sh install-docker.sh

- After this installation, a group called as docker is created. all   the users who are part of this group can use docker.

- Lets add a current user to docker group.

 sudo usermod -aG docker <username>

- Exit and relogin

- now execute docker info .

 ### Containerize the application

- This means ensuring application developed (by your org) is running inside container.

- This also means we need to create a image (docker image) of our application.

## How to build images

- To build a docker image first know the manual steps involved in bringing up your application.

- Once we have steps, then we have two approaches in building images
  manual approach which involved creating a container & taking a snapshot (commit).
  automatable & repetitive approach referred as Dockerfile approach.

## Lets build a docker image to have openjdk 17

- Findout the steps involved in installing openjdk 17 on
ubuntu:

 sudo apt update
 sudo apt install openjdk-17-jdk -y

# Manual approach with ubuntu

- pull ubuntu image

 docker image pull ubuntu:24.04

- Now create a container in an interactive mode

 docker container run -it --name ubuntujava ubuntu:24.04 /bin/bash

- Now run the commands
 
 apt update
 apt install openjdk-17-jdk -y 

- verify if java is installed

 java -version

- Now exit from container and execute commit command to create image.

 docker container commit ubuntujava jdk17:ubuntu

- Lets create a container using new image and cross check if java is present or not.

 docker container run -it jdk17:ubuntu /bin/bash
 java -version

