---
title: "Jenkins"
datePublished: Sat Nov 11 2023 19:19:38 GMT+0000 (Coordinated Universal Time)
cuid: cloufkxuk000109jn0m22021i
slug: jenkins
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699730370680/1f0eac89-b5dd-4c02-be00-da213db890ff.png
tags: jenkins, aws-ec2, jenkins-installation

---

What is Jenkins?

It is a open source automation tool. It is used **to continually create and test software projects**, making it easier for developers and DevOps engineers to integrate changes to the project and for consumers to get a new build.

It is based on java language, it works on port number 8080.

Why It is used?

Jenkins will continually test your builds and alert you to any mistakes early in the process.

Practical 1:

How to Install Jenkins with the Help of AWS EC2 (AMI - Ubuntu)

## [AWS EC2 Instance](https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero/blob/main/README.md#aws-ec2-instance)

* Go to AWS Console
    
* Instances(running)
    
* Launch instances
    

[![Screenshot 2023-02-01 at 12 37 45 PM](https://user-images.githubusercontent.com/43399466/215974891-196abfe9-ace0-407b-abd2-adcffe218e3f.png align="left")](https://user-images.githubusercontent.com/43399466/215974891-196abfe9-ace0-407b-abd2-adcffe218e3f.png)

### [Install Jenkins.](https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero/blob/main/README.md#install-jenkins)

Pre-Requisites:

* Java (JDK)
    

### [Run the below commands to install Java and Jenkins](https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero/blob/main/README.md#run-the-below-commands-to-install-java-and-jenkins)

Install Java

```plaintext
sudo apt update
sudo apt install openjdk-11-jre
```

Verify Java is Installed

```plaintext
java -version
```

Now, you can proceed with installing Jenkins

```plaintext
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

**Note:** By default, Jenkins will not be accessible to the external world due to the inbound traffic restriction by AWS. Open port 8080 in the inbound traffic rules as show below.

* EC2 &gt; Instances &gt; Click on
    
* In the bottom tabs -&gt; Click on Security
    
* Security groups
    
* Add inbound traffic rules as shown in the image (you can just allow TCP 8080 as well, in my case, I allowed `All traffic`).
    

[![Screenshot 2023-02-01 at 12 42 01 PM](https://user-images.githubusercontent.com/43399466/215975712-2fc569cb-9d76-49b4-9345-d8b62187aa22.png align="left")](https://user-images.githubusercontent.com/43399466/215975712-2fc569cb-9d76-49b4-9345-d8b62187aa22.png)

### [Login to Jenkins using the below URL:](https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero/blob/main/README.md#login-to-jenkins-using-the-below-url)

http://:8080 \[You can get the ec2-instance-public-ip-address from your AWS EC2 console page\]

Note: If you are not interested in allowing `All Traffic` to your EC2 instance 1. Delete the inbound traffic rule for your instance 2. Edit the inbound traffic rule to only allow custom TCP port `8080`

After you login to Jenkins, - Run the command to copy the Jenkins Admin Password - `sudo cat /var/lib/jenkins/secrets/initialAdminPassword` - Enter the Administrator password

[![Screenshot 2023-02-01 at 10 56 25 AM](https://user-images.githubusercontent.com/43399466/215959008-3ebca431-1f14-4d81-9f12-6bb232bfbee3.png align="left")](https://user-images.githubusercontent.com/43399466/215959008-3ebca431-1f14-4d81-9f12-6bb232bfbee3.png)

### [Click on Install suggested plugins](https://github.com/iam-veeramalla/Jenkins-Zero-To-Hero/blob/main/README.md#click-on-install-suggested-plugins)

[![Screenshot 2023-02-01 at 10 58 40 AM](https://user-images.githubusercontent.com/43399466/215959294-047eadef-7e64-4795-bd3b-b1efb0375988.png align="left")](https://user-images.githubusercontent.com/43399466/215959294-047eadef-7e64-4795-bd3b-b1efb0375988.png)

Wait for the Jenkins to Install suggested plugins

[![Screenshot 2023-02-01 at 10 59 31 AM](https://user-images.githubusercontent.com/43399466/215959398-344b5721-28ec-47a5-8908-b698e435608d.png align="left")](https://user-images.githubusercontent.com/43399466/215959398-344b5721-28ec-47a5-8908-b698e435608d.png)

Create First Admin User or Skip the step \[If you want to use this Jenkins instance for future use-cases as well, better to create admin user\]

[![Screenshot 2023-02-01 at 11 02 09 AM](https://user-images.githubusercontent.com/43399466/215959757-403246c8-e739-4103-9265-6bdab418013e.png align="left")](https://user-images.githubusercontent.com/43399466/215959757-403246c8-e739-4103-9265-6bdab418013e.png)

Jenkins Installation is Successful. You can now starting using the Jenkins

[![Screenshot 2023-02-01 at 11 14 13 AM](https://user-images.githubusercontent.com/43399466/215961440-3f13f82b-61a2-4117-88bc-0da265a67fa7.png align="left")](https://user-images.githubusercontent.com/43399466/215961440-3f13f82b-61a2-4117-88bc-0da265a67fa7.png)

## Now you can run jenkins easily on this virtual machine.