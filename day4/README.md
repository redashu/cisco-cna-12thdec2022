## Revision 

<img src="rev.png">

### problem with container clustering option 

<img src="prob.png">

### Introduction to KAAS -- Kubernetes as a service in CLoud nativ architecture 

<img src="kaas.png">

### k8s architecture 

<img src="k8sarch.png">

### to store container images 

<img src="reg.png">

### pushing container app image to docker hub 

```
ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker images 
REPOSITORY       TAG          IMAGE ID       CREATED        SIZE
ashishapp        imgv1        4df2e572b7b5   22 hours ago   145MB
bhushan          imgv1        240b5a404a42   22 hours ago   145MB
manishwebapp     frontendv1   c43e475a2d3f   23 hours ago   145MB
navneetwebapp    uiv1         fffc8f77e40e   23 hours ago   145MB
vijaywebapp      uiv1         7dbb885828a3   23 hours ago   145MB
sameerappnginx   imgv1        0e5095c90b82   23 hours ago   145MB
nikiwebapp       uiv1         5a45a21bd2e2   23 hours ago   145MB
ashuwebapp       uiv1         4c8bab215383   23 hours ago   145MB
mysql            latest       7484689f290f   8 days ago     538MB
adminer          latest       ef63a68bb1a5   4 weeks ago    91.3MB
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ 
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker  tag  ashuwebapp:uiv1   docker.io/dockerashu/ashuwebapp:uiv1 
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker login 
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: dockerashu
Password: 
WARNING! Your password will be stored unencrypted in /home/ashu/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded

===
ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker  push  docker.io/dockerashu/ashuwebapp:uiv1
The push refers to repository [docker.io/dockerashu/ashuwebapp]
545afc9364bf: Pushed 
e83791f03918: Mounted from library/nginx 
10e506a84718: Mounted from library/nginx 
9485bb85a132: Mounted from library/nginx 
47064e0edc59: Mounted from library/nginx 
5678f6b95362: Mounted from library/nginx 
b5ebffba54d3: Mounted from library/nginx 
uiv1: digest: sha256:9744988c8120279d646b7db5d0ab6c3a92437ddfacb478b8e753aa7b435384c3 size: 1781

==
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker logout 
Removing login credentials for https://index.docker.io/v1/
```




