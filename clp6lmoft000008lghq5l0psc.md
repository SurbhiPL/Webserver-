---
title: "Docker"
datePublished: Mon Nov 20 2023 07:42:11 GMT+0000 (Coordinated Universal Time)
cuid: clp6lmoft000008lghq5l0psc
slug: docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700417763656/8c0fd211-6720-40c3-abc1-8434e1253a65.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1700417925784/87b2fce4-ec02-4c63-91b6-d44ff70708fb.png
tags: docker, devops-tools, learning-journey, basics-of-docker

---

Have you ever been intimidated by Docker’s fancy name and wondered what it is? — Great, This post is for you.

In this post, we will cover what exactly this devil is and what it does.

First and foremost, what is Docker? 🧐

***Docker*** is an open platform that enables users to develop, ship, and run applications with ease.

Docker is a platform that enables developers to automate the deployment of applications inside lightweight, portable containers. Containers are a form of lightweight virtualization that packages an application and its dependencies together, ensuring consistent and reproducible environments across different systems.

**Key Concepts:**

1. **Image:**
    
    * An image is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, including the code, runtime, libraries, and system tools.
        
2. **Container:**
    
    * A container is a running instance of a Docker image. It encapsulates the application and its dependencies, ensuring consistency and portability across various environments.
        
3. **Dockerfile:**
    
    * A Dockerfile is a script that contains instructions for building a Docker image. It specifies the base image, adds application code, sets environment variables, and configures other settings.
        
4. **Registry:**
    
    * A registry is a centralized repository for storing and distributing Docker images. Docker Hub is a public registry, and private registries can also be set up for internal use.
        
    
    ## Install docker with the Help of AWS EC2 (ubuntu AMI) virtual machine.
    
    Here's a step-by-step guide to install Docker on an Amazon EC2 instance and run a simple container:
    
    ### **Step 1: Launch an EC2 Instance**
    
    1. Log in to the AWS Management Console.
        
    2. Navigate to the EC2 dashboard.
        
    3. Click "Launch Instance" and choose an Amazon Machine Image (AMI). Select an image that suits your needs, such as "Amazon Linux 2" or "Amazon Linux 2 LTS."
        
    
    ### **Step 2: Connect to the EC2 Instance**
    
    1. Once the instance is running, connect to it using SSH. Use the key pair you selected during the instance launch.
        
        ```basic
        ssh -i YourKeyPair.pem ec2-user@your-ec2-instance-ip
        ```
        
    
    ### **Step 3: Install Docker on EC2 Instance**
    
    For Amazon Linux 2:
    
    ```basic
    sudo yum update -y
    sudo amazon-linux-extras install docker
    sudo service docker start
    sudo usermod -aG docker ec2-user
    ```
    
    For Ubuntu:
    
    ```basic
    sudo apt-get update
    sudo apt-get install docker.io
    sudo systemctl start docker
    sudo systemctl enable docker
    sudo usermod -aG docker ubuntu
    ```
    
    For CentOS:
    
    ```basic
    sudo yum update -y
    sudo yum install docker -y
    sudo systemctl start docker
    sudo systemctl enable docker
    sudo usermod -aG docker centos
    ```
    
    ### **Step 4: Verify Docker Installation**
    
    ```basic
    docker --version
    docker info
    ```
    
    ### **Step 5: Run a Simple Docker Container**
    
    Let's run the official Nginx web server as a simple example:
    
    ```basic
    docker run -d -p 80:80 --name mynginx nginx
    ```
    
    This command does the following:
    
    * `-d`: Run the container in the background.
        
    * `-p 80:80`: Map port 80 from the host to port 80 in the container.
        
    * `--name mynginx`: Assign the name "mynginx" to the container.
        
    * `nginx`: Use the official Nginx image from Docker Hub.
        
    
    ### **Step 6: Access Nginx in the Browser**
    
    Open your web browser and navigate to [`http://your-ec2-instance-ip`](http://your-ec2-instance-ip). You should see the default Nginx welcome page.
    
    ### **Step 7: Cleanup (Optional)**
    
    If you want to stop and remove the container:
    
    ```basic
    bashCopy codedocker stop mynginx
    docker rm mynginx
    ```
    
    Remember to replace `YourKeyPair.pem` and `your-ec2-instance-ip` with your actual key pair and EC2 instance information.
    
    This is a basic example, but it demonstrates the process of installing Docker on an EC2 instance, running a container, and accessing the application. Depending on your application requirements, you may need to expose additional ports or configure other Docker options.