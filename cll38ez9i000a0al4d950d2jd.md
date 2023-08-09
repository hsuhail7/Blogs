---
title: "Understand  Core Component of Active Directory: FSMO Roles and AD Partition"
datePublished: Wed Aug 09 2023 04:30:09 GMT+0000 (Coordinated Universal Time)
cuid: cll38ez9i000a0al4d950d2jd
slug: understand-core-component-of-active-directory-fsmo-roles-and-ad-partition
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691509058144/0a8dfeb8-67f5-4f9c-8aab-756f0f8ee938.jpeg
tags: microsoft, server, windows, it, active-directory

---

**FSMO** (**F**lexible **S**ingle **M**aster **O**perations)

When a new Active Directory environment is created from scratch the Active Directory Installation wizard(dcpromo) adds five FSMO roles so a forest with one domain has five roles. These are the following 5 FSMO Roles:

* **Schema Master**
    
* **Domain Naming master**
    
* **PDC Emulator**
    
* **RID Master**
    
* **Infrastructure Master**
    

However, these roles are divided into 2 categories:

* Forest-wide
    
    * Schema Master
        
    * Domain Naming Master
        
* Domain-wide
    
    * Primary Domain Controller(PDC)
        
    * Relative Identifier Master(RID)
        
    * Infrastructure Master(IM)
        

```plaintext
#Command to check FSMO roles owner:
netdom query fsmo

#command to check PDC in the domain
netdom query pdc
```

**Schema Master**

The Domain Controller which holds the Schema Master role is responsible for performing updates to the directory schema, that is, schema naming context or LDAP://cn=schema,cn=configuration,dc=&lt;domain&gt;. This DC is the only one that can process updates to the directory schema. Once the Schema update is complete, it's replicated from the schema master to all other DCs in the directory. Also, Changes once performed cannot be reverted. This is a forest-wide role

**Domain naming Master**

The Domain Controller which holds the Domain Naming master role is responsible for the creation and deletion of existing and new Domains in the Forest. Domain Name that is, Configuration naming context or LDAP://CN=Partitions, CN=Configuration, DC=&lt;domain&gt;. This is a forest-wide role.

**PDC Emulator**

The PDC emulator is necessary to synchronize time in an enterprise because time service is required by the Kerberos authentication protocol. The PDC emulator of a domain is authoritative for the domain. The PDC emulator at the root of the forest becomes authoritative for the enterprise and should be configured to gather the time from an external source. PDC emulator role holder retains the following functions:

* Password changes done by other DCs in the domain are replicated preferentially to the PDC emulator.
    
* When authentication failures occur at a given DC because of an incorrect password, the failures are forwarded to the PDC emulator before a bad password failure message is reported to the user.
    
* Account lockout is processed on the PDC emulator.
    

**RID Master(Relative Identifier)**

The main purpose of the RID Master is to allocate sequences of relative IDs to other domain controllers in the same domain. The RID Master allocates chunks (blocks of 500) of these relative IDs to the DCs as needed. When a particular DC is low or out of relative IDs, it will contact the RID Master to obtain another chunk.

Whenever a new object such as a user, group, or computer object is created a **Security Identifier(SID)** is assigned to the object. This SID is made up of Domain GUID and RID number provided by the domain controller.

**Infrastructure Master**

The infrastructure Master is responsible for maintaining references to objects in other domains. It ensures that cross-domain object references are accurate and up-to-date.

**AD Partitions**

There are three main types of partitions:

* **Domain Partition**: Contains information specific to a single domain within the forest. This includes user accounts, groups, and other objects related to that domain.
    
* **Configuration Partition**: Stores information about the forest's overall structure, including domain and site configurations. It helps ensure consistency across the entire forest.
    
* **Schema Partition**: Holds the AD schema, defining object classes and attributes that can be used to create objects within the directory.
    
* Application Partition(Optional partition): This is an optional partition it can be configured to replicate Forest-wide, Domain-wide or specific servers within a forest.
    
    example: DNS Integration with AD
    

**Conclusion**

FSMO Roles and AD Partition are very important part of Active Directory as it helps in managing Active Directory Environment. if you have suggestions please share that with us or if you want us to write on any other topic do let us know.