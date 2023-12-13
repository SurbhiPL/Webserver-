---
title: "Mini Project - 3"
datePublished: Thu Dec 07 2023 03:30:12 GMT+0000 (Coordinated Universal Time)
cuid: clpun446x000007jx0ri05tuv
slug: mini-project-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701370209927/f352776d-44a5-4be8-b00c-4c5744cd0d95.png
tags: ec2, aws, practice, devops, apache, miniprojects

---

# **Hosting a Web Server on Amazon Web Services (AWS) Elastic Compute Cloud (EC2) and creating own website.**

Tools Used: Apache, AWS EC2,

Step1: Launch AWS EC2

My-Web-Servere - Instance Name

T2 Micro - Instance Type

Key pair - create - use putty for windows / other wise create a pem

Allow http and https in security group

SSh is a protocol which is used to connect with remote linux servers

Https/http are use to access websites on the webservers

Wait for sometime to come up instance in running instance with Status 2/2 check pass.

Connectinon of Instance -

Connect with EC2 instance

or Use putty if u have ppk key pair

**sudo apt-get update**

**sudo apt install apache2**

**/which apache2 or apache -v**

**sudo service apache2 start**

**sudo service apache2 status**

Instatus we can check **active** is there

and connect with Public IP you will see the apache test page if not please chech all the steps again

change the directory

cd /var/www/html

ls

rm index.html

nano index.html

you can write ur own content

"Hi This is tiya"

Now ctrl +x to save and exit

after that go to the public IP and connect you can see your content.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701369098139/9f013c52-a70a-498c-80fd-a9c991786b14.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701369054755/c98bf97c-35fc-47c6-8ded-61a40840fa6f.png align="center")