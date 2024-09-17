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

2. Install Jenkins
   
   2.1 sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
 
   2.2 sudo apt-get install Jenkins
     
   2.3 sudo systemctl enable jenkins
  
   2.4 sudo systemctl start jenkins

   2.5 sudo apt-get install docker.io  -y

   2.6 sudo systemctl enable docker

   2.7 sudo systemctl start docker

   2.8 sudo su -

   Grant Jenkins user and Ubuntu user permission to docker deamon.

   2.9 usermod -aG docker jenkins

   3.0 usermod -aG docker ubuntu
   
 
4. Install Jenkins plugins

   3.1 docker pipeline

   3.2 sonarqube scanner

   3.3 pipeline stage view

   3.4 open blue ocean




5. Create a new Jenkins pipeline:

   4.1 Name-Pipeline ultimate-demo  type pipeline
   
   4.2 Advance project option-Pipeline scrpit from scm

   4.3 Scm-git  URL-https://github.com/sharfuddin1986/Jenkins_CICD  Branch-main 

   4.4 Script path-java-maven-sonar-argocd-helm-k8s/spring-boot-app/JenkinsFile

 ##  Define the pipeline stages:
    Stage 1: Checkout the source code from Git.
    Stage 2: Build the Java application using Maven.
    Stage 3: Run unit tests using JUnit and Mockito.
    Stage 4: Run SonarQube analysis to check the code quality.
    Stage 5: Package the application into a JAR file.
    Stage 6: Deploy the application to a test environment using Helm.
    Stage 7: Run user acceptance tests on the deployed application.
    Stage 8: Promote the application to a production environment using Argo CD.

## Configure Jenkins pipeline stages:
    Stage 1: Use the Git plugin to check out the source code from the Git repository.
    Stage 2: Use the Maven Integration plugin to build the Java application.
    Stage 3: Use the JUnit and Mockito plugins to run unit tests.
    Stage 4: Use the SonarQube plugin to analyze the code quality of the Java application.
    Stage 5: Use the Maven Integration plugin to package the application into a JAR file.
    Stage 6: Use the Kubernetes Continuous Deploy plugin to deploy the application to a test environment using Helm.
    Stage 7: Use a testing framework like Selenium to run user acceptance tests on the deployed application.
    Stage 8: Use Argo CD to promote the application to a production environment.
     


5. Configure SonarQube on same ec2 instance:

   5.1 sudo su-

   5.2 adduser sonarqube

   5.3 wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.4.0.54424.zip

   5.4 sudo apt-get install unzip
   
   5.5 unzip *

   5.6 chmod -R 755 /home/sonarqube/sonarqube-9.4.0.54424

   5.7 chown -R sonarqube:sonarqube /home/sonarqube/sonarqube-9.4.0.54424

   5.8 cd sonarqube-9.4.0.54424/bin/linux-x86-64/

   5.9 ./sonar.sh start

       !! Now you can access the SonarQube Server on http://<ip-address>:9000

       Go to my account create access token !! Name-jenkins  create token and copy token


6.  Add credential in jenkins for sonarqube,Dockerhub and Github access token
   

    6.1 Manage jenkins-credential-system-add credential-kind  secret  and secret  paste the sonarqube access token save

    6.2 Add credential-kind user name & password- id- docker-cred(all ready define in pipeline) 

        user name-dockerhub account user name  password- dockerhub account password save

   6.3 Add credential- kind-secret text and secret- paste the git hub access token save 






