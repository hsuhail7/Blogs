---
title: "Understanding File Permissions in Linux 📚"
datePublished: Sat Aug 12 2023 14:57:25 GMT+0000 (Coordinated Universal Time)
cuid: cll8557qc000b08mj20nc2jrl
slug: understanding-file-permissions-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691837903328/3f45b98d-541e-455a-9208-c7af661e36d4.webp
tags: linux, linux-for-beginners, linux-basics, 90daysofdevops, tws

---

### Introduction

File permissions in Linux play an important role in maintaining the security and access control of files and directories. Due to this permission, an individual can access, modify, or execute your files. These permissions are represented by a combination of letters and dashes which helps you to understand the permission level on file Let's try to understand more about File permissions.

### Different Types of File Permission **📜**

* Owner/User permission: The user permission only belongs to the owner of the file.
    
* Group Permission: This permission applies to the group that has been associated with the file.
    
* Others Permission: This permission applies to other users or you can say everyone else.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691837578462/11b6817d-5434-4b5d-bf33-f4b0c272a2ae.jpeg align="center")

### Decoding File Permission in Linux

Permission for user, group and others is represented using this notation

`r : Read`

`w : Write`

`x : Execute`

`- : No Permission`

Here's how the notation works in real-world **🌐**

Here we have a file dev.txt and we will see the permission level for owner, group and others.

```plaintext
ubuntu@ip-172-31-91-127:~/Test_Op$ ls -l
-rw-rw-r-- 1 ubuntu ubuntu    0 Aug 12 10:33 dev.txt
```

Let's break down these permissions

```plaintext
-   : By this permission we understand if this is a File or Directory
rw- : In this permisison we can see User have Read and Write Permissions only.
rw- : In this permission we can Group have Read and Write Permissions only
r-- : In this permission we can Others have Read Permissions only
```

Few more examples:

```plaintext
ubuntu@ip-172-31-91-127:~/Test_Op$ ls -l
drwxrwxr-x 2 ubuntu ubuntu 4096 Aug 11 06:21 backup
-rwxrw-r-- 1 ubuntu ubuntu  374 Aug 11 06:31 backup_work.sh
```

```plaintext
Permission on Backup Directory
drwxrwxr-x 2 ubuntu ubuntu 4096 Aug 11 06:21 backup

d: Since this is a Directory we see a d representation.
rwx: User ubunutu has Read, Write and Execure permission.
rw-: Group ubunutu has Read, Write and Execure permission.
r--: Others have user Read permission only.
```

```plaintext
Permission on backup_work.sh File
-rwxrw-r-- 1 ubuntu ubuntu  374 Aug 11 06:31 backup_work.sh
-  : Since there is no representation so its a File
rwx: For User ubunutu have Read, Write and Execure permissions.
rw-: For Group ubunutu we have Read and Write permissions. 
r--: For Others we have Read Permission only.
```

### Managing Extended File Access Control Lists

In Linux, an access control list (ACL) constitutes a list of permissions linked to an entity. These lists prove invaluable when conventional file permission frameworks fall short. ACLs empower you to allocate permissions to specific users or groups, irrespective of their alignment with the entity's proprietor or group.

These are the two commands `getfacl` and `setfacl` in Linux, which is used for managing extended file access control lists (ACLs).

However, when you try to run the command on your Linux machine it will give you an error.

```plaintext
ubuntu@ip-172-31-91-127:~/Test_Op$ getfacl dev.txt
Command 'getfacl' not found, but can be installed with:
sudo apt install acl
```

To resolve this you have to install the acl package and this is how it looks

```plaintext
ubuntu@ip-172-31-91-127:~/Test_Op$ sudo apt-get install acl
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  acl
0 upgraded, 1 newly installed, 0 to remove and 48 not upgraded.
Need to get 38.5 kB of archives.
After this operation, 205 kB of additional disk space will be used.
Get:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu jammy/main amd64 acl amd64 2.3.1-1 [38.5 kB]
Fetched 38.5 kB in 0s (2274 kB/s)
Selecting previously unselected package acl.
(Reading database ... 94052 files and directories currently installed.)
Preparing to unpack .../archives/acl_2.3.1-1_amd64.deb ...
Unpacking acl (2.3.1-1) ...
Setting up acl (2.3.1-1) ...
Processing triggers for man-db (2.10.2-1) ...
Scanning processes...
Scanning linux images...

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
```

Now you will be able to run getfacl and setfacl for the files.

```plaintext
ubuntu@ip-172-31-91-127:~/Test_Op$ getfacl dev.txt
# file: dev.txt
# owner: ubuntu
# group: ubuntu
user::rw-
group::rw-
other::r--
```

Depending upon your Distribution you have to install the package accordingly

```plaintext
Distribution	Command
Debian	        apt-get install acl
Ubuntu	        apt-get install acl
Alpine	        apk add acl
Arch Linux	    pacman -S acl
Kali Linux	    apt-get install acl
CentOS	        yum install acl
Fedora	        dnf install acl
Raspbian	    apt-get install acl
```

I hope this blog will help you to understand how permission level and acl are used in the Linux system however there is more related file permission like changing file ownership, changing groups associated with a file and also related to Others which we will include in the next blog. Please share your suggestions with us so that we can improve our blog.