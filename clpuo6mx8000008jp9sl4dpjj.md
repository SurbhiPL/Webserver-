---
title: "Mini Project - 1"
datePublished: Thu Dec 07 2023 04:00:10 GMT+0000 (Coordinated Universal Time)
cuid: clpuo6mx8000008jp9sl4dpjj
slug: mini-project-1
tags: ec2, docker, aws, devops, jenkins

---

# **Deploying web app using Jenkins CI/CD declarative pipeline.**

1\. First of all, go to the AWS portal, and create a new instance. As

· Name: myjenkins

· AMI: ubuntu.

· Instance type: t2.micro (free tier).

· Key pair login: Create &gt; docker.pem.

· rest all by default

· (Download the .pem file.)

· Click on Launch Instance.

2\. Now, we will allow ports 8080 and 8001 for this machine from a security group. We can find the security group in the VM description. Now, here we need to allow “Inbound Rule”

3\. Now, connect to the EC2 instance that you have created. Copy the SSH from the server:

![](https://miro.medium.com/v2/resize:fit:841/0*bS80y2BRFJl9Qp3p align="left")

4\. Go to the download folder, where the .pem file is placed and open the terminal in the same location, and paste the SSH.

5\. Install Jenkins from the following link:

[https://www.jenkins.io/doc/book/installing/linux/](https://www.jenkins.io/doc/book/installing/linux/)

or you can go to my previous artical //[https://hashnode.com/post/cloufkxuk000109jn0m22021i](https://hashnode.com/post/cloufkxuk000109jn0m22021i)

6\. Install Docker by running:

“Sudo apt-install [docker.io](https://www.jenkins.io/doc/book/installing/linux/)”

7\. Now check if it got installed by running “jenkins — version” and “docker — version”

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701331035016/bca20d25-63c3-4693-bb8b-2f5695e97e55.png align="center")

8\. Goto Jenkins Dashboard and Click on “New Item”

· Name: declarative\_pipeline

· Select: Pipeline

Description: This is a demo pipeline project.

9\. Pipeline Script:

pipeline{

agent any

stages{

stage{

steps{

git branch: ‘main’, URL: ‘[https://github.com/SurbhiPL/Demo-App.git](https://github.com/SurbhiPL/Demo-App.git)'

}

}

stage{

steps{

echo “Testing”

}

}

stage{

steps{

script{

sh “docker build — no-cache -t react\_django\_demo\_app .”

}

}

}

stage{

steps{

script{

sh “docker run -p 8001:8001 -d react\_django\_demo\_app”

}

}

}

}

}

![](https://miro.medium.com/v2/resize:fit:875/0*CeK0NvX_GuRBeGD3 align="left")

10\. Click on “Save”.

11\. Click on “Build Now”.

![](https://miro.medium.com/v2/resize:fit:875/0*x1XtlhlcvceEMN-G align="left")

12\. We can click on “Stage View” to check the results if it is still under process.

![](https://miro.medium.com/v2/resize:fit:875/0*-FrIKzmdc5tdQk4I align="left")

13\. Once it will be completed, It will return as “Success”.

![](https://miro.medium.com/v2/resize:fit:875/0*hPycVDwUFntv9lxr align="left")

14\. Now, Search for the Public IP with port 8001 in the browser,

![](https://miro.medium.com/v2/resize:fit:875/0*3ir-_qfJ3_P_7b1v align="left")

We have built the image of a Web app source code, and deployed that image as a container, using Jenkins Pipelines.

Hope you found this helpful. Do connect/ follow for more such content.