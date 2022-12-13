## lets get started 

### Introduction to PAAS

<img src="paas.png">

### FAAS 

<img src="faas.png">
 

### Introduction to MonoLith app design and deployment 

<img src="mono.png">

## breaking Mono-lith -- intro micro components or services 

<img src="micro.png">


### Micro services as component in VM -- gonna give below problems 

<img src="vmprob.png">

### journey to containers & introduction to CAAS

<img src="caas.png">

### Introduction to containers vs vm 

<img src="vmcn.png">

### Introduction CRE -- container runtime Engine 

<img src="cre.png">

### installing docker engine in amazon vm 

```
[ec2-user@ip-172-31-31-82 ~]$ sudo -i
[root@ip-172-31-31-82 ~]# 
[root@ip-172-31-31-82 ~]# 
[root@ip-172-31-31-82 ~]# yum  install docker -y 
Failed to set locale, defaulting to C
Loaded plugins: extras_suggestions, langpacks, priorities, update-motd
Resolving Dependencies
--> Running transaction check
---> Package docker.x86_64 0:20.10.17-1.amzn2.0.1 will be installed
--> Processing Dependency: runc >= 1.0.0 for package: docker-20.10.17-1.amzn2.0.1.x86_64
--> Processing Dependency: libcgroup >= 0.40.rc1-5.15 for package: docker-20.10.17-1.amzn2.0.1.x86_64
--> Processing Dependency: containerd >= 1.3
```

### starting docker engine 

```
[root@ip-172-31-31-82 ~]# systemctl start docker 
[root@ip-172-31-31-82 ~]# systemctl status docker 
● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2022-12-13 09:37:57 UTC; 4s ago
     Docs: https://docs.docker.com
  Process: 3656 ExecStartPre=/usr/libexec/docker/docker-setup-runtimes.sh (code=exited, status=0/SUCCESS)
  Process: 3653 ExecStartPre=/bin/mkdir -p /run/docker (code=exited, status=0/SUCCESS)
 Main PID: 3658 (dockerd)
    Tasks: 8
   Memory: 22.5M
   CGroup: /system.slice/docker.service
           └─3658 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock --default-ulimit nofile=32768:65...

Dec 13 09:37:55 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:55.265005043Z" level=info msg="Cli...grpc
Dec 13 09:37:56 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:56.639216690Z" level=warning msg="...ght"
Dec 13 09:37:56 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:56.639259746Z" level=warning msg="...ice"
Dec 13 09:37:56 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:56.639452817Z" level=info msg="Loa...rt."
Dec 13 09:37:57 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:57.158898507Z" level=info msg="Def...ess"
Dec 13 09:37:57 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:57.237077419Z" level=info msg="Loa...ne."
Dec 13 09:37:57 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:57.251812219Z" level=info msg="Doc...0.17
Dec 13 09:37:57 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:57.251909601Z" level=info msg="Dae...ion"
Dec 13 09:37:57 ip-172-31-31-82.ec2.internal systemd[1]: Started Docker Application Container Engine.
Dec 13 09:37:57 ip-172-31-31-82.ec2.internal dockerd[3658]: time="2022-12-13T09:37:57.279133681Z" level=info msg="API...ock"
Hint: Some lines were ellipsized, use -l to show in full.
[root@ip-172-31-31-82 ~]# systemctl enable docker 
Created symlink from /etc/systemd/system/multi-use
```

### creating users and giving access of docker 

```
[root@ip-172-31-31-82 ~]# for i  in ashu ashish bhushan manish rameez naga navneet nikitha sameer vijay 
> do
> useradd $i
> echo "CiscoCn@098#"  |  passwd $i --stdin 
> usermod -aG docker $i 
> done 
Changing password for user ashu.
passwd: all authentication tokens updated successfully.
Changing password for user ashish.
passwd: all authentication tokens updated successfully.
Changing password for user bhushan.
passwd: all authentication tokens updated successfully.
Changing password for user manish.
passwd: all authentication tokens updated successfully.
Changing password for user rameez.
passwd: all authentication tokens updated successfully.
```

### access docker from non root user 

```
[ashu@ip-172-31-31-82 ~]$ whoami
ashu
[ashu@ip-172-31-31-82 ~]$ docker  version 
Client:
 Version:           20.10.17
 API version:       1.41
 Go version:        go1.18.6
 Git commit:        100c701
 Built:             Wed Sep 28 23:10:17 2022
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server:
 Engine:
  Version:          20.10.17
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.18.6
  Git commit:       a89b842
  Built:            Wed Sep 28 23:10:55 2022
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.6.8
  GitCommit:        9cd3357b7fd7218e4aec3eae239db1f68a5a6ec6
 runc:
  Version:          1.1.4
  GitCommit:        5fd4c4d144137e991c4acebb2146ab1483a97925
 docker-init:

```

### COntainerization of application 

<img src="cont1.png">

## web app containerization 

### lets take sample code 

```
git clone https://github.com/schoolofdevops/html-sample-app.git
   12  ls
   13  git clone https://github.com/yenchiah/project-website-template.git
```

### choose any application from above and Introduce dockerfile in it 

### Dockerfile -- content 
```
FROM nginx 
# we are refering to standard docker image 
LABEL name=ashutoshh
LABEL email=ashutoshh@linux.com 
COPY . /usr/share/nginx/html/
```

### lets build this code  + dockerfile --into a container image 

```
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ ls
html-sample-app  project-website-template
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ ls  html-sample-app/
assets  Dockerfile  elements.html  generic.html  html5up-phantom.zip  httpd.dockerfile  images  index.html  LICENSE.txt  README.txt
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ 
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker build  -t  ashuapp:imgv1  html-sample-app/ 
Sending build context to Docker daemon   3.63MB
Step 1/4 : FROM nginx
latest: Pulling from library/nginx
025c56f98b67: Pull complete 
ca9c7f45d396: Pull complete 
ed6bd111fc08: Pull complete 
e25b13a5f70d: Pull complete 
9bbabac55ab6: Pull complete 
e5c9ba265ded: Pull complete 
Digest: sha256:ab589a3c466e347b1c0573be23356676df90cd7ce2dbf6ec332a5f0a8b5e59db
Status: Downloaded newer image for nginx:latest
 ---> ac8efec875ce
Step 2/4 : LABEL name=ashutoshh
 ---> Running in 0a32d7b6cbf0
Removing intermediate container 0a32d7b6cbf0
 ---> f1626d1767c0
Step 3/4 : LABEL email=ashutoshh@linux.com
 ---> Running in 5e0bedbcce4e
Removing intermediate container 5e0bedbcce4e
 ---> d0aba755f0df
Step 4/4 : COPY . /usr/share/nginx/html/
 ---> 92768a90d00b
Successfully built 92768a90d00b
Successfully tagged ashuapp:imgv1
```




