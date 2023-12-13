---
title: "Mini Project - 2"
datePublished: Thu Dec 07 2023 04:00:11 GMT+0000 (Coordinated Universal Time)
cuid: clpuo6nut000008l4b7ep5s3i
slug: mini-project-2
tags: docker, github, learning, devops, ebs, miniprojects, game-2048

---

# **Deployment of 2048 Game on AWS using docker**

![](https://miro.medium.com/v2/resize:fit:875/1*6H2FvsHeFRxdzOyYU7p4vg.png align="left")

In this article we will be deploying the game “2048” using Docker and Amazon Web Services (AWS). we’ll go through the step-by-step process of containerizing the 2048 game and then seamlessly deploying it onto the AWS platform.

## **The tools utilized in this project are as follows:**

1. Github
    
2. Visual Studio Code
    
3. Docker
    
4. AWS -Elastic Beanstalk
    
    ## The tutorial will be in two parts:
    
    1. Containerization of the application and deployment using Docker.
        
    2. Deployment using the AWS Elastic Beanstalk
        
    
    The Github Repo for the project to be deployed, the **2048 Game** can be found in the link below.
    

Now we move on to containerization of the application using Docker on the running EC2 instance.

1. First, Install Docker and Docker runtime on the EC2 instance.
    

P.S: Installation of Docker is out of the scope of this article but you can find a detailed process [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04).

After installing docker, run the code below to ensure Docker is running successfully on your EC2 instance. You should get a message like that in the picture below saying Docker is “active (running)”.

```plaintext
sudo systemctl status docker
```

![](https://miro.medium.com/v2/resize:fit:875/1*2mnELFJ54sku5tEzJY2apQ.png align="left")

2\. Go ahead to create a file in a folder called “2048". This file will serve as the Dockerfile where the commands to build our Docker image will reside in.

```plaintext
mkdir 2048
cd 2048
nano Dockerfile
```

3\. The “nano” command will create the Dockerfile and open it at the same time. Next type the following script in the Dockerfile.

```plaintext
FROM ubuntu:22.04
RUN apt-get update
RUN apt-get install -y nginx zip curl
RUN echo "daemon off;">>/etc/nginx/nginx.conf
RUN curl -o /var/www/html/master.zip -L https://codeload.github.com/jabir000/2048/zip/master
RUN cd /var/www/html/ && unzip master.zip && mv 2048-master/* . && rm -rf 2048-master master.zip
EXPOSE 80
CMD ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]
```

4\. Save and exit the file

5\. Then, let’s build our docker image by executing the following command

```powershell
docker build -t "docker image name" .
```

![](https://miro.medium.com/v2/resize:fit:875/1*Bn0Gl8rwaN8yP0On4g_5wQ.png align="left")

Successfully building the docker image

6\. Confirm the docker image has been successfully built

```plaintext
sudo docker images
```

![](https://miro.medium.com/v2/resize:fit:824/1*KOzd46TAv4AIQgN7RfhNwA.png align="left")

7\. Next, we are going to spin up an instance of the docker image (Container) on port 80.

```plaintext
docker run -d -p 80:80 "container id"
```

![](https://miro.medium.com/v2/resize:fit:875/1*oHetc9jZfvttlv-fTX2M4w.png align="left")

8\. Check if your container has been created successfully.

```plaintext
docker ps
```

You should have something similar if your container has been successfully created.

![](https://miro.medium.com/v2/resize:fit:875/1*JYCt-d4rbBQcHgvc0Tv6wA.png align="left")

Go on to access your application on http://&lt;External IP Address of EC2&gt;:80

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701680484300/5a9d07f3-c1d7-4eea-800c-f1d7194a7597.png align="center")

**We have successfully deployed the 2048 Game by containerization using Docker.**

**Deployment of the 2048 Game using AWS Elastic Beanstalk**

The *AWS Elastic Beanstalk* is one of the many fully managed services on the AWS cloud that aids the easy deployment and scaling of web applications and services developed with Python, Ruby, Go, Java, PHP, .NET and Node.js. With the AWS Elastic Beanstalk, developers are able to access a quick means of deploying and managing applications in the AWS Cloud without having to worry about the underlying infrastructure where the application will be deployed.

AWS Elastic Beanstalk offers many benefits for developers in terms of rapid deployment and ease of management. Some of these include:

* Automatic Deployment.
    
* Automatic Scaling
    
* Automatic and detailed capacity provisioning.
    
* Web Application health monitoring
    
* Automatic Load Balancing
    
    In this section, we will deploy the 2048 number game using AWS Elastic Beanstalk.
    
    ***Recall we deployed the same web application using Docker in the first section of this tutorial. A functional React Application.***
    
    ## **Step 1: Make environment configurations.**
    
    1. Go to your AWS Management console and search for Elastic Beanstalk in the service menu. Then, click the *Create Application* button on the default page of the AWS Elastic Beanstalk service.
        
    
    Elastic Beanstalk service
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919812283/81bbb182-69c2-4685-bedc-f38a2426bd43.png align="center")
    
    2\. Choose the *Web server environment* as your environment tier and name your application accordingly. With the Application name, the environment name is filled and you can then add an environment description.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919796763/13e63da3-99e8-40cd-a0c6-8536618b1460.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919755266/284a8c71-93f0-4ba0-843e-1e9b14ce8201.png align="center")
    
    3\. Go ahead to configure the platform as a “Managed Platform” and Platofrm type to be “Docker”, then select the recommended version of Docker.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919731427/942186c4-a8c6-448b-b8a8-bf263ffad76a.png align="center")
    
    4\. Moving on to the application code section, using your VS Code, recreate the Docker file used in the first section on your local PC. This will then be uploaded as the application code.
    
    Choose the *Upload your code* option and add a version label for each deployment you make on AWS Elastic Beanstalk.
    
    ![](https://miro.medium.com/v2/resize:fit:875/1*mmtEA0FWDvgN5Uqj8X1YmQ.png align="left")
    
    5\. Choose the “Single Instance (Free Tier Eligible)” as your configuration presets.
    
    ## **Step 2: Configure service access.**
    
    1. Select the “Use an existing service role”, then go on to create an EC2 Instance profile in the IAM console with the required permissions for AWS Elastic Beanstalk as listed below.
        
    
    a. **AWSElasticBeanstalkWebTier**
    
    b. **AWSElasticBeanstalkWorkerTier**
    
    c. **AWSElasticBeanstalkMulticontainerDocker**
    
    In this case, I have created an EC2 Instance profile named ***“aws-elasticbeanstalk-ec2-role”***
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919705689/e00d771f-fbe0-4c01-afb2-b05ef2ebd6bd.png align="center")
    
    ## **Step 3: Setup Networking, databases and tags.**
    
    P.S Do not use the default vpc, so ensure you create your own custom vpc with the necessary inbound rules on the security group allowing HTTP/HTTPS traffic.
    
    Choose the custom VPC you created and a Public subnet for the instance settings.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919685182/8692b192-0baf-44cb-a92d-ca642f5388c5.png align="center")
    
    Leave every other option as default then ***Skip to review.***
    
    ## **Step 4: Review your configurations**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919641375/62b167cc-e26e-42ab-a2b5-69f097eb9893.png align="center")
    
    Review the configurations made and then Submit.
    
    ## **Step 5: Monitor the environment creation**
    
    The environment creation process is initiated. Wait for some minutes for the environment to be successfully created.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919626867/5b8e2f11-82d6-497a-a1f7-3bffbb6c7226.png align="center")
    
    Once the environment is successfully created, load the domain to access the web application.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701919601052/e685167e-b726-41e5-9709-84db68e72b95.png align="center")
    
    **The 2048 Game has been successfully deployed using AWS Elastic Beanstalk.**
    
    ***Thank you for reading!***