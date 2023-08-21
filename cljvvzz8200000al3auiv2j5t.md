---
title: "Jenkins Live Project  with Declarative CI/CD Pipeline with Groovy syntax using env. variable"
seoTitle: "Jenkins"
datePublished: Sun Jul 09 2023 20:28:28 GMT+0000 (Coordinated Universal Time)
cuid: cljvvzz8200000al3auiv2j5t
slug: jenkins-live-project-with-declarative-cicd-pipeline-with-groovy-syntax-using-env-variable
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688930464028/a8d9272a-f7d7-4c50-a25f-96136ee6c343.jpeg
tags: aws, devops, devops-articles, 90daysofdevops, trainwithshubham

---

![Jenkins Pipeline là gì ? Tổng quan Jenkins Pipeline CI/CD - Technology ...](https://cuongquach.com/wp-content/uploads/2019/11/jenkins-pipeline-la-gi.jpg align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688931098573/f153c27e-c0f6-4f16-9536-40d9a0ef9d62.png align="center")

Launch an EC2 instance and install Jenkins. Use this instance as a Jenkins server using the t2-micro instance type.

ssh -i "jenkins-key.pem" [ubuntu@ec2-13-232-61-41.ap-south-1.compute.amazonaws.com](mailto:ubuntu@ec2-13-232-61-41.ap-south-1.compute.amazonaws.com)(SSH into the jenkins server.)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688932433696/f2187465-70d9-4f90-9eea-8a5ab9afbaba.png align="center")

Use the code from Github **"django-notes-app".**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688931252468/3624448c-56c4-4156-b67e-08333d5e0157.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688929167484/28b058d7-4502-4e8c-bdc0-bf9359d446b8.png align="center")

**“sh” is used for Groovy syntax for shell command**

**Used the special syntax to use the env. variable to login**

withCredentials(\[usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")\]){

**withCredentials-function, which gives the password through the ID (env. variable)**

**sh "docker tag my-note-app $env.dockerHubUser/my-note-app:latest"**

\[Tag with your username and upload it to Docker Hub with the latest version.\]

**sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"**

Login to the docker hub with the above command

**sh "docker push $env.dockerHubUser/my-note-app:latest"**

This will push the code to the Docker hub.

`echo "Deploying the container"`

`sh "docker-compose down && docker-compose up -d"`

`sh "docker run -d 8000:8000 anuraglovesdocker/my-note-app:latest"`

docker run detached mode publish port 8000 system 8000 container

Note: Open port 8000 in NSG and use the public IP for running on the website

echo "Deploying the container"

**sh "docker-compose down and docker-compose up -d"**

**<mark>To make the website more robust, since when we run the website, it runs on the same port 8000, which is already</mark>** [**<mark>allocated. So</mark>**](http://allocated.So) **<mark>we need to use Docker Compose, which will shut down the existing port 8000 and open it again.</mark>**

**<mark>Docker Compose is a special type of YML</mark>** [**<mark>file. It</mark>**](http://file.It) **<mark>can run multiple containers, and it will be managed by Docker Compose.</mark>**

**build : . --- build in the same file**

**It creates a service called web."**

**The docker build and docker run commands are managed in build: and ports:**

`sudo apt-get install docker-compose --to install`

**At the deploy stage, the docker container is down (removes previous container)**

**Updated**

**Then goes up**

`sh "docker-compose down and docker-compose up -d"`

Add the image from the Docker Hub to the Docker compose

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688931382657/61550788-27ae-4f70-a4f9-9b301eddba19.png align="center")

$ git clone the repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688932211824/b9941a9b-f796-4622-b8c6-801e911382fa.png align="center")

`$sudo apt install docker`

`$ sudo apt install docker-compose` ( it is a special type of yml file that runs multiple containers.)

***change directory and cat docker-compose.yml***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688928439848/2fb40cbe-e5aa-4594-a747-9b4ff92aa492.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688933832022/676b31a9-6ff4-48cd-b1d2-01e49106a321.png align="center")

Using Docker compose makes a pipeline robust as it builds and pushes it to the Docker Hub (note: you need to have an account in the Docker Hub).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688929821923/bcd03af7-34cb-4353-8b1b-9b1873c91dcc.png align="center")

Start and setup Jenkins for CI/CD integration (https://\*13.232.61.41:8080 once it is allowed from the security group in AWS)

![Comment installer Jenkins sur Ubuntu 16.04](https://assets.digitalocean.com/articles/jenkins-install-ubuntu-1604/jenkins-plugins.png align="left")

Use the Pipeline script from SCM ( GitHub repository "[django-notes-app/Jenkinsfile at main · Anurag2022github/django-notes-app](https://github.com/Anurag2022github/django-notes-app/blob/main/Jenkinsfile)")

Branch -main

***<mark>Jenkinsfile is added, which contains the declarative pipeline (groovy syntax)</mark>***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688930690603/233ee39a-9765-4a6d-ada4-f4f149e7624d.png align="center")

*<mark>Using the env. variable hides your passwords in Groovy syntax. Use the credential ID.</mark>*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688929547262/7a62ca2b-0a52-47c1-abff-81b688e176a3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688932919985/97116b10-851d-452e-8362-12ac95c37842.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688932862477/5cbd9152-66a7-4686-85c5-2c8ce628738d.png align="center")

**Webhooks in GitHub allow developers to receive real-time notifications about events occurring within a repository. They enable the automatic triggering of actions, such as updating external systems, integrating with continuous integration and continuous deployment (CI/CD) pipelines, or sending notifications to external services.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688934164299/047f0dba-73b9-4f82-b9b5-215d9592d11f.png align="center")

payload URL will have the Jenkins URL,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688934246055/a999a0f9-34e6-4f35-882d-b037f4ae7a44.png align="center")

Automates continuous deployment Any change in the GitHub code commit will change the CI/CD deployment at the end-to-end level.

Declarative checkout SCM **Clone CodeBuildPush to Docker HubDeploy**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688928082292/5fd74629-711f-4d99-bd5e-d637c0c64d57.png align="center")

[http://13.232.61.41:8000/](http://13.232.61.41:8000/) Use the public IP of the Jenkins server with **port 8000** allowed in **AWS security groups (inbound rules to allow network traffic )**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688928623131/1de94ab1-9df7-40ae-b35d-b3e95037d65e.png align="center")

**Congratulations !!! Your application is up and ready!**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688928713616/0e31bb37-166d-4998-84c7-5489e7508742.png align="center")