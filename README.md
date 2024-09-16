## Jenkins Pipeline for Java based application using Maven, SonarQube, Argo CD, Helm and Kubernetes

![diagram.jpg](https://github.com/user-attachments/assets/10c96b59-bea4-48d7-ba30-b7a1b89fb284)


Here are the step-by-step details to set up an end-to-end Jenkins pipeline for a Java application using SonarQube, Argo CD, helm, and Kubernetes:

Prerequisites:

- AWS EC2 instance minimum 2 core cpu and 8 G.B Ram Ubuntu 24.0 os

- Java application code hosted on a Git repository

- Jenkins server

- SonarQube Server

- Kubernetes cluster

- Helm package manager

- Argo CD
  
## Steps:


1. Clone the git repository and install java
 
   1.1 git clone https://github.com/sharfuddin1986/Jenkins_CICD.git
   
   1.2 sudo apt update
   
   1.3 sudo apt install openjdk-17-jre
   
   1.4 java –version

3. Install Jenkins
   
   2.1 sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
 
  2.2 sudo apt-get install Jenkins
     
  2.3 sudo systemctl enable jenkins
  
  2.4 sudo systemctl start jenkins
   
   
   
