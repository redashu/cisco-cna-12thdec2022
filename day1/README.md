## lets get started 

### targeting things 

<img src="target.png">

### app testing / deployment problems in your Past 

<img src="app-p.png">

### Introduction virtualization using Hypervisor tech -- 

<img src="hyper.png">

### type of hypervisor 

<img src="type.png">

### list of t1 & t2 

<img src="t1t2.png">

## Introduction to cloud computing delivery model services 

<img src="del.png">

### understanding  delivery model in detail

<img src="del1.png">

### public vs private cloud deployment models 

<img src="pub.png">

---

### private 

<img src="pri.png">

## users / accounts in cloud env

<img src="u.png">

## Understanding Cloud Regions 

<img src="region.png">

### understanding av zones under particular region 

<img src="avz.png">

### lets connect linux vm from mac client 

```
fire@ashutoshhs-MacBook-Air ~ % ls  -l  Downloads/ashu-cisco-private-key.pem 
-rw-r--r--@ 1 fire  staff  1674 Dec 12 12:53 Downloads/ashu-cisco-private-key.pem
fire@ashutoshhs-MacBook-Air ~ % 
fire@ashutoshhs-MacBook-Air ~ % chmod 400 Downloads/ashu-cisco-private-key.pem 
fire@ashutoshhs-MacBook-Air ~ % 
fire@ashutoshhs-MacBook-Air ~ % ssh -i Downloads/ashu-cisco-private-key.pem  ec2-user@3.86.138.22  
The authenticity of host '3.86.138.22 (3.86.138.22)' can't be established.
ECDSA key fingerprint is SHA256:JpCRBgvtv3buDMAjCgEwH0ZUgk5gVxaKgqzFmTHi8yI.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '3.86.138.22' (ECDSA) to the list of known hosts.

       __|  __|_  )
       _|  (     /   Amazon Linux 2 AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-2/
19 package(s) needed for security, out of 31 available
Run "sudo yum update" to apply all updates.
-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory
[ec2-user@ip-172-31-88-17 ~]$ whoam
-bash: whoam: command not found
[ec2-user@ip-172-31-88-17 ~]$ whoami
ec2-user
[ec2-user@ip-172-31-88-17 ~]$ uname 
Linux
[ec2-user@ip-172-31-88-17 ~]$ uname -r
5.10.147-133.644.amzn2.x86_64
[ec2-user@ip-172-31-88-17 ~]$ 

```




