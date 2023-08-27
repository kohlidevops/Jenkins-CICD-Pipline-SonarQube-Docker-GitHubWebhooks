# Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks

Launch Jenkins CICD Server

Step -1: Launch Jenkins CICD server

To launch EC2 ubuntu-22 instance with T3.medium in AWS cloud.

Step -2: SSH to Jenkins Server

To SSH to machine and update the ubuntu system.

#sudo apt-get update -y

Jenkins will work on Java run time, So we need to install the Java in Jenkins CICD server.

#sudo apt-get install openjdk-11-jre -y

Step -3: Install Jenkins 

#curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

#echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
  
#sudo apt-get update

#sudo apt-get install jenkins

Use below link to copy/paste the installation steps

https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/blob/main/install-jenkins.sh

Step -4: To access the Jenkins web console

To access the jenkins console with Jenkins server IP with Port 8080 and unlock the jenkins 

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/510cd689-bfba-4347-8cd6-9dc5b80ac0d1)

Install the suggested plugins

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/d74a32a6-3c8e-4524-b80a-a873dce64d5e)

To create a first admin user then save and continue

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/669f91f0-55c5-423e-ac83-ffecda029259)

Step -5: Create a free-style project

Let's create a free-stle project in Jenkins console and configure the Soure code management

Please clone the project from below github link

https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks.git

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/592d8703-11ca-4e81-bcfd-0dbb669456c9)

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/32d32a5c-0431-4592-a1ed-418b85e5733a)

Choose the "GitHub hook trigger for GITSCM polling". So when any changes the code in GitHub then automatically Jenkins pull the code from GitHub to build and test the code.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/93be09e1-40a2-43b6-8a1c-4173e20afdc2)

Then save the project and run the build manually to ensure everything working fine

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/5d532082-01dc-4805-91b8-81e84829f235)

Perfect! The build has been succeeded. Now automate this process through enabling webhooks in GitHub. So Whenever any changes code in GitHub then automatically build will happen. Let's create a webhook for GitHub project.

Step -6: To create a GitHub webhook

Navigate to GitHub and select your project - settings - webhooks - add the Jenkins URL in payload URL with /github-webhook/.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/417adaad-b38e-44b1-84c9-d7a57d5bc042)

Select "Let me select individual events" and choose Pullrequests and Pushes, Then Add Webhooks to complete this process.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/b1366c3d-6988-4154-bd32-80cf4a9fed1b)

Let's create the test file in GitHub project to ensure the Jenkins build has been started automatically. To do this, create one testfile and commit the changes in GitHub and monitor the Jenkins build.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/120ea1b5-d6f4-4511-8007-162c23af13bd)

Here we go, the Jenkins build has been automatically started as we expected too.

Step -7: Configure Sonarqube

Launch one more EC2 ubuntu instance with t3.medium for Sonarqube application and update the system.

#sudo apt-get update -y

#sudo apt-get upgrade -y

Please follow below link to install and configure Sonarqube service.

https://www.fosstechnix.com/how-to-install-sonarqube-on-ubuntu-22-04-lts/

After installation, you can access the sonarqube through IP with Port 9000. By default, sonarqube username is admin and password is admin.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/a4ef85c9-3f7e-445c-b002-b397356f7e54)

After than, you can change your default password.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/19d30527-d6e2-455d-b902-66941315aaed)

Then setup with Manually option

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/6a97b7de-4b7a-4bc1-a791-32adddea498e)

To create a project name and key then setup this project.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/65771498-35fa-4b4f-a2ad-1c496393c112)

Next I need to integrate my CI tool. Here GitHub is my case.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/1debcafe-105c-4786-acc8-b36a44345927)

Choose continue to next step.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/1171baf5-11f1-4c99-84bf-bd58f5da1ebd)

Next, To create a Workflow yaml. For my case, i need to go with other (for js,...) and copy/paste the project key in notepad for later use.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/b34a01a2-0de5-4663-9b9b-f63e38f92968)

**sonar.projectKey=Mywebsite**

Next, Finish this tutorail to complete this process.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/084ede11-5c81-431a-8386-9481409fef69)

Choose - My Account 

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/651c0ac8-52f9-45d6-8efb-a8442749f5e5)

then select - security - to generate a tokens for your project and copy/paste it in notepad for later use.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/2a0a4d93-2cc3-40c0-aeca-4990f7207b43)

**sqp_3709a74a3c5b21ddf28fbe806da749e188f61265**

Step -8: Install plugins in Jenkins

Go back to Jenkins console and install the below plugins

**SSH2 Easy**

**SonarQube Scanner**

step -9: Configure Sonarqube scanner

Navigate to Jenkins console and select Tools then scroll all the way down and update the Sonarqube Scanner.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/6f68a1a6-f99e-423f-ab77-8a698f3a356f)

step -10: Configure Sonarqube server

Navigate to Jenkins console and select Manage Jenkins then select System to configure Sonarqube server.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/667ccb94-842c-447d-8f58-b97a3bd3f03c)

step -11: Configure Sonarqube in project

Select you project in Jenkins - choose - Configure - go to Build steps - select - Execute Sonarqube scanner

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/058ca0aa-17e6-4983-a045-90264bed0f96)

Then save it and back to Configure system in Jenkins (Manage Jenkins - System) and update the Server Authentication Token in Sonarqube installation using Add - Jenkins

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/43986adb-2082-44ab-b257-7fcf56d4075d)

This is the token which was generated in Sonarqube console

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/d2e5f700-8330-42d8-bff1-8b4bc0db1ce9)

Add this Token and Save the System

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/d0127093-def5-4e23-a3ec-cf1fe324d4be)

Step -12: Build and Test

To ensure the code has been tested with Sonarqube after the build the project.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/a503b0ad-d810-4435-80f4-a1c555e073f4)

Build has been succeded as well code has been validated from Sonarqube. Let me check with Sonarqube console.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/0e1f1786-2460-4906-ad28-069540fb98db)

Perfect! The code has been Passed with Sonarqube test. Hereafter, we need to setup the docker server to deploy our application once the build and test has been succeded.

Step -13: Configure Docker Server

Launch one ubuntu EC2 instance with t3.micro and install the docker service on it.

#sudo apt-get update -y

#sudo apt-get install ca-certificates curl gnupg

#sudo install -m 0755 -d /etc/apt/keyrings

#curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

#sudo chmod a+r /etc/apt/keyrings/docker.gpg

#echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#sudo apt-get update

#sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

#docker --version

To update the SSHD config in Docker server

To update the SSHD config to access the docker server from Jenkins server with SSH

#sudo -i

#sudo nano /etc/ssh/sshd_config

open the file to uncomment

**PubkeyAuthentication yes**

and change the value from No to Yes

**PasswordAuthentication yes**

save and exit then restart the SSHD

#sudo systemctl restart sshd

To change the password for user ubuntu in Docker server

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/e6a3959a-11c5-4707-91be-4206b7b7512f)

Step -14: To access the Docker server from Jenkins Server with password

To access the docker server from jenkins server using ssh with password. Login to Jenkins machine through SSH.

#sudo passwd jenkins

#su - jenkins

#ssh ubuntu@<docker-server-ip>

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/759ee4df-9222-4eea-a5b9-4d06dc3fae93)

Yes, I can able to login to docker machine

Step -15: To access the docker server from Jenkins Server without password

To do so, We need to ssh-keygen to generate the SSH key in Jenkins machine then it should copy to the target <docker> machine.

#ssh-keygen

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/2c8d2e6b-5119-4d97-80f6-b35904e3e85b)

#ssh-copy-id ubuntu@<docker-server-ip>

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/724b01bb-1102-4cb8-b32e-dd6fa577fde9)

Now, I can able to login to docker server from jenkins server through SSH without password.(Because we are using ssh key here to login)

Step -16: To add Server Group Center in Jenkins console

Navigate to jenkins console - select - Manage jenkins - System - scroll down - look at the Server Group Center

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/cd2b57d9-6848-4553-b278-44877c59319d)

My docker server username is ubuntu and type the password what was set in docker server. Then apply and save it.

Step -17: To configure the Server List

Navigate to jenkins console - select - Manage jenkins - System - scroll down - look at the Server List. Now add your Docker server.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/bb2e0c67-447c-4bda-8bd3-c9e577640b5d)

Then apply and save it.

Step -18: To configure the Remote Shell

To configure the Remote shell in your project which was created in Jenkins console. Select your project - configure - Build Steps - Choose Remote Shell

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/4602c753-26ae-4a56-9c79-815bca9fcad8)

Then touch command to create one test file from jenkins project and build this project again and check in docker server whether file has been created or not.

Perfect! My build has been succeeded. 

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/f77370d9-cacc-40e5-89f9-7d39cb7a9e5f)

Let me check with my docker machine

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/0a82593c-9c13-412a-ab0b-46cdc5682322)

File has been created in docker machine

Step -19: Create a Docker file

To create a docker file in your repository.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/b13cecc2-c46b-4696-9a58-c8a9c39ebe32)

In this Docker file, im just using nginx image and copying the current directory files to /usr/share/nginx/html/ folder.

Step -20: To copy files using SCP

To copy a currect directory files in jenkins server to docker server using SCP command in Build execute shell. To do so, first create one directory called website in docker server with below path

#mkdir website

#cd website

#pwd

#/home/ubuntu/website

Back to Jenkins console and select your project - configure. This time remove Remote Shell from the project (Because we have configured Remote Shell to ensure whether we can create a file in docker server).

#scp -r ./* ubuntu@52.66.242.179:~/website/

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/1f4c991a-9fc6-4aa1-8448-0a2e27a29ae9)

I just copying the all the files in the current directory of jenkins build server to remote server (docker server). Then save and run the build. 

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/a4cb7628-5cd2-4d52-801f-00c221124337)

Yup! Everything has been copied from jenkins (/var/lib/jenkins/workspace/Automated-Pipeline/) to docker server inside /home/ubuntu/website/ folder.

Step -21: To add a user to docker group

By default, the ubuntu user has no permission to access the docker. So we need to add the user ubuntu to docker group in docker server.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/53576043-264d-4816-a977-2e74052cda9f)

#sudo usermod -aG docker ubuntu

#newgrp docker

#docker ps

Step -22: To add a Remote shell

To add a Remote Shell in Jenkins console to configure docker to run a container

#cd /home/ubuntu/website/

#docker build -t mywebsite .

#docker run -d -p 8090:80 --name=mywebapp mywebsite

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/30a2259b-3656-4230-8e61-be5ad2e63ec2)

I just instructed that first change directory to my website directory then build the docker image using docker file. After the image processing, to run the docker container using docker image and port mapping for Host(EC2 instance) is 8090 and 80 for container port.

Build again. After the build succeeded, i can able to see the running conatiner in docker server.

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/10042f6f-d6bb-4bad-80e5-cb8b2f1a0fea)

If I access the container from browser, Yes I can access

![image](https://github.com/kohlidevops/Jenkins-CICD-Pipline-SonarQube-Docker-GitHubWebhooks/assets/100069489/9e12a341-4643-418d-9517-c3fd606a24eb)


