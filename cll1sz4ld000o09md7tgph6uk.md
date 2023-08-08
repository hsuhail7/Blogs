---
title: "Understand Core Component of Active Directory: Organization Units and Containers"
datePublished: Tue Aug 08 2023 04:30:09 GMT+0000 (Coordinated Universal Time)
cuid: cll1sz4ld000o09md7tgph6uk
slug: understand-core-component-of-active-directory-organization-units-and-containers
tags: microsoft, windows, active-directory, windows-server

---

**Organizational Units (OUs)** 🗄️

Organizational Units are containers within Active Directory that allow you to logically organize objects, such as users, computers, and groups. OUs provide a hierarchical structure that mirrors your organization's real-world departments or divisions.

Example:  
Consider a company named "Fabrikam.com" that uses Active Directory to manage its resources. They have created OUs and sub-OUs to manage their resources like computers, users and so on.

OU - Prod &gt; Sub-OU Computers &gt; Sub-OU Workstations

OU - Prod &gt; Sub-OU Computers &gt; Sub-OU Servers

OU - Prod &gt; Sub-OU users

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691404020244/15ed6a8c-d52b-40a0-92b7-d44ef30361ae.png align="center")

Note: In any Active Directory environment we have default containers as well which are created automatically when an Active Directory environment is created.

The following are referred to as Default Containers :

* Users
    
* Computers
    
* Domain Controllers
    
* System
    
* LostAndFound
    

Whenever you create a new user or join a computer machine in a domain it will automatically place the object in the respective container either Users or Computers.

Note: we cannot directly link any GPO with a Default Container so you can try these options:

1. Move the object from Container to an OU and then try to link GPO with this new OU.
    
2. Link GPO at the Domain level and try to check if that applies to the computer or user containers.
    

I hope this blog would help you understand the importance of Organization Units and Default Containers in Active Directory. If you have any questions or would like to share your experiences, feel free to leave a comment below.