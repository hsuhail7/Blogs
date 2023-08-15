---
title: "Setting Up Docker and Jenkins on Ubuntu  Ubuntu 22.04.3 A Beginner-Friendly Guide 🐳"
datePublished: Tue Aug 15 2023 13:54:44 GMT+0000 (Coordinated Universal Time)
cuid: cllcd85eu000309l94mphawo2
slug: setting-up-docker-and-jenkins-on-ubuntu-ubuntu-22043-a-beginner-friendly-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692107643509/c8968a46-ccae-4ea1-ba82-b529ae5cdb41.png
tags: docker, devops, jenkins, devops-articles, 90daysofdevops

---

### Introduction

In this blog, we will share how Docker and Jenkins can be installed on a Ubuntu machine by and beginner. we have provided step-by-step guidance for your reference:

### Installing Docker 🐳

1. Open Terminal on your machine and run the below command:
    

```plaintext
sudo apt install docker
```

1. Once Docker is installed you can verify the Docker service status
    

```plaintext
  systemctl status docker

ubuntu@ip-172-31-91-127:~/Learning_Devops/Learning_Devops/Day7$ systemctl status docker
● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2023-08-12 14:18:27 UTC; 1h 38min ago
```

1. However, If you want to STOP/START/RESTART Docker service you should <mark>use sudo systemctl otherwise the password is required</mark> as shown below
    

```plaintext
systemctl stop docker
ubuntu@ip-172-31-91-127:~/Learning_Devops/Learning_Devops/Day7$ systemctl stop docker
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to stop 'docker.service'.
Authenticating as: Ubuntu (ubuntu)
Password:

sudo systemctl stop docker
```

Also while checking running the docker ps command you will get a permission denied error reason is the user is not a member of the docker group

```plaintext
docker ps
ubuntu@ip-172-31-91-127:~/Learning_Devops/Learning_Devops/Day7$ docker ps
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json": dial unix /var/run/docker.sock: connect: permission denied

#User is added as a member of docker group
sudo usermod -aG docker $USER
ubuntu@ip-172-31-91-127:~/Learning_Devops/Learning_Devops/Day7$ sudo usermod -aG docker $USER
```

1. Now Restart your machine and docker ps will work fine
    

```plaintext
ubuntu@ip-172-31-91-127:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

### **Installing Jenkins** 🚀

For Ubuntu distribution, there are some pre-requisite that needs to be followed before installing Jenkins.

For Jenkins installation, we have some requirement which we mentioned in below steps and needs to be followed:

```plaintext
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \/usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

```plaintext
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \https://pkg.jenkins.io/debian-stable binary/ | sudo tee \/etc/apt/sources.list.d/jenkins.list > /dev/null
```

```plaintext
sudo apt-get update
```

```plaintext
sudo apt-get install jenkins
```

checking service status systemctl status Jenkins

```plaintext
ubuntu@ip-172-31-91-127:~$ systemctl status jenkins
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: activating (start) since Tue 2023-08-15 13:39:17 UTC; 14s ago
   Main PID: 1204 (java)
      Tasks: 40 (limit: 1121)
     Memory: 210.6M
        CPU: 13.967s
     CGroup: /system.slice/jenkins.service
             └─1204 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/java/jenkins.war --webroot=/var/cache/jenkins/war --httpP>
```

Congratulation!

you have successfully installed Docker and Jenkins on your Ubuntu machine. Please share your feedback and suggestions we will appreciate it. Now try the same steps on your machine and lets us know your response.