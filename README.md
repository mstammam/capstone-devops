# Udacity AWS Cloud DevOps Nanodegree

#My github repo:

https://github.com/mstammam/capstone-devops.git

-----------------------------------------------------------------------------------------

## Project Overview

 In this project, I used rolling deployment and I run through the following topics in order to complete the project.

1)	Working in AWS
2)	Using Jenkins to implement Continuous Integration and Continuous Deployment 
3)	Building pipelines 
4)	Working with EKS. 
5)	Building Kubernetes clusters 
6)	Building Docker containers in pipelines 
-----------------------------------------------------------------------------------------

##1## Build docker and Kubernetes locally: 

./run_docker.sh and go to localhost:8000 to check your app
-----------------------------------------------------------------------------------------

##2## Upload docker
./upload_docker.sh
-----------------------------------------------------------------------------------------

##3## Run Minikube and kubernetes:
minikube start
./run_kubernetes.sh
-----------------------------------------------------------------------------------------

##4## Create kubernetes cluster using EKS:

eksctl create cluster --name tammam-capstone-cluster --node-type t2.micro --region us-east-2

aws eks update-kubeconfig --name tammam-capstone-cluster

kubectl config use-context arn:aws:eks:us-east-2:796848775042:cluster/tammam-capstone-cluster

kubectl apply -f deployment/deployment.yml
-----------------------------------------------------------------------------------------

##5## Install jenkins:

sudo apt update
sudo apt upgrade
sudo apt install default-jdk
sudo wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins
sudo systemctl status jenkins
-----------------------------------------------------------------------------------------

##6## Install jenkins plugins:

install aws pipeline plugins
install blueocean plugins and other required plugins.


##7## Restart Jenkins
sudo systemctl restart jenkins
-----------------------------------------------------------------------------------------
##8## Connect Jenkins with aws and Dockerhub accounts:
add global credentials for aws
add global credentials for dockerhub.
-----------------------------------------------------------------------------------------
##9## Create jenkinsfile that include the following:
lint HTML
Push Docker Image
Deploy Container
-----------------------------------------------------------------------------------------
##10## Connect pipeline with github account.
##11## Add pipeline trigger to trigger the pipeline every time github updated (1 min. interval)
##12## Test your pipeline.  

