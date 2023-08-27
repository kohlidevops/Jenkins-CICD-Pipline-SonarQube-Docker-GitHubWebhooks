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

