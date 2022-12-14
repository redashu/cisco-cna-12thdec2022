## Revision 

<img src="rev.png">

### app containerization 

<img src="appc.png">

### source code to image -- containers 

<img src="cont1.png">

### lets build our first image for simple webapp 

```
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ ls
html-sample-app  project-website-template
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker  build  -t  ashuwebapp:1.0 html-sample-app/ 
Sending build context to Docker daemon   3.63MB
Step 1/4 : FROM nginx
latest: Pulling from library/nginx
025c56f98b67: Pull complete 
ec0f5d052824: Pull complete 
cc9fb8360807: Pull complete 
defc9ba04d7c: Pull complete 
885556963dad: Pull complete 
f12443e5c9f7: Pull complete 
Digest: sha256:75263be7e5846fc69cb6c42553ff9c93d653d769b94917dbda71d42d3f3c00d3
Status: Downloaded newer image for nginx:latest
 ---> 3964ce7b8458
Step 2/4 : LABEL name=ashutoshh
 ---> Running in 1188f56fb92e
Removing intermediate container 1188f56fb92e
 ---> 22ee66a8fb9b
Step 3/4 : LABEL email=ashutoshh@linux.com
 ---> Running in 7bb2ec1e2cef
Removing intermediate container 7bb2ec1e2cef
 ---> 6f33ed975965
Step 4/4 : COPY .  /usr/share/nginx/html/
 ---> 6eb142224809
Successfully built 6eb142224809
Successfully tagged ashuwebapp:1.0
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker  images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
ashuwebapp   1.0       6eb142224809   28 seconds ago   145MB
nginx        latest    3964ce7b8458   4 hours ago      142MB
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ 
```

## to create containers -- we need things 

<img src="need.png">

### creating container 

```
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker run -d --name ashuappc1 -p 1234:80  ashuwebapp:1.0 
e11bc8c63a2586da61ec2061992f01b83eb42a8603e6f722a129aea774b18991
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker ps
CONTAINER ID   IMAGE            COMMAND                  CREATED         STATUS        PORTS                                   NAMES
e11bc8c63a25   ashuwebapp:1.0   "/docker-entrypoint.…"   3 seconds ago   Up 1 second   0.0.0.0:1234->80/tcp, :::1234->80/tcp   ashuappc1
```

### Container networking 

<img src="cnet1.png">

### checking default CNM bridges by docker 

```
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker  network  ls
NETWORK ID     NAME      DRIVER    SCOPE
2bdd732d1ae7   bridge    bridge    local
144a88b41bb1   host      host      local
1139e95a707e   none      null      local
```

### checking containers connected in default bridge

```
[ashu@ip-172-31-31-82 ashu-microservices-apps]$ docker  network  inspect  2bdd732d1ae7 
[
    {
        "Name": "bridge",
        "Id": "2bdd732d1ae75035aa9653ecb4fe63263e9170e975dfc300507edf0c17a3a231",
        "Created": "2022-12-14T04:19:10.315772151Z",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": null,
            "Config": [
                {
                    "Subnet": "172.17.0.0/16",
                    "Gateway": "172.17.0.1"
                }
            ]
        },
        "Internal": false,
        "Attachable": false,
        "Ingress": false,
        "ConfigFrom": {
            "Network": ""
        },
        "ConfigOnly": false,
        "Containers": {
            "2fed110e27a87d6c0b3b595d22eae54b03fddb6453bcd6b93234cae30aa816cc": {
                "Name": "BhushanCont",
                "EndpointID": "9edde90996f0e8aced1316b996032f75c5caa3d7566b8f72783e2fda391b9ac5",
                "MacAddress": "02:42:ac:11:00:08",
                "IPv4Address": "172.17.0.8/16",
                "IPv6Address": ""
            },
            "3b55d503aae4fda3e6ed09074d6f5f93b6b14e69af307e0d0a78c2d481720c6f": {
                "Name": "nikiappc1",
                "EndpointID": "a71043feb08ba6b2e5c0a3cdb3ef43f6a78bc8ed6c8d438d837c73857c48295c",
                "MacAddress": "02:42:ac:11:00:03",
                "IPv4Address": "172.17.0.3/16",
                "IPv6Address": ""
            },
            "3d4962b99f0f1b5af7b693edada50d3970c221e000b035999415c14e66d76c12": {
                "Name": "vijayapp",
                "EndpointID": "66680ac320dd60ad777e9145da870340358179efef81de8c4571b4870a7666bd",
                "MacAddress": "02:42:ac:11:00:0a",
                "IPv4Address": "172.17.0.10/16",
                "IPv6Address": ""
            },
            "640c831e3ebc02280917e5eac8c51fae7d474731649568f522b79c188b7d34b7": {
                "Name": "naga_container",
                "EndpointID": "5332dea6bf5076a1436bf9eb70b88b3123c063d37a1cdb716832f75160f0a6bd",
                "MacAddress": "02:42:ac:11:00:07",
                "IPv4Address": "172.17.0.7/16",
                "IPv6Address": ""
            },
            "6f6d3da0394ca0291c869e86b1e2d423e375f3a341e4ea5c6e568e8cc5907d19": {
                "Name": "manish-cont1",
                "EndpointID": "7701cce388140a80754e60a5b14f7aa83986a7ec4bf3d7f059adf513a86510f8",
                "MacAddress": "02:42:ac:11:00:05",
                "IPv4Address": "172.17.0.5/16",
                "IPv6Address": ""
            },
            "817d9236ac47d308d4255271bc417d36a3cea1222b9ed05375b90b7656b3d191": {
                "Name": "sameerCont",
                "EndpointID": "fccbf6152d9ac22ae61fac33c67fbcd44b9c031e30ccd79eb398e62254a4aa0b",
                "MacAddress": "02:42:ac:11:00:09",
                "IPv4Address": "172.17.0.9/16",
                "IPv6Address": ""
            },
            "8a0f267b28d6385b7fd6a407569026584da800242bb7a9d8b261778154cfbab0": {
                "Name": "navneetapppc1",
                "EndpointID": "ead1b0a14f28569ddc247a3f53d971d0e086fc5d69a5bb4a5dba78e2f1397e17",
                "MacAddress": "02:42:ac:11:00:06",
                "IPv4Address": "172.17.0.6/16",
                "IPv6Address": ""
            },
            "e11bc8c63a2586da61ec2061992f01b83eb42a8603e6f722a129aea774b18991": {
                "Name": "ashuappc1",
                "EndpointID": "017943283a9d4bd7426ce93f6a3eca2068d6bf1a43c805edb2b68b1a5624a38e",
                "MacAddress": "02:42:ac:11:00:02",
                "IPv4Address": "172.17.0.2/16",
                "IPv6Address": ""
            },
            "e6cf12042219dde6533324da49ae840de43b57d1a9b8b5c397d2333600562219": {
                "Name": "ashishappv1",
                "EndpointID": "a2e8c2df10c732d6fe2cdf46d0aceeda96f900ba0c057dd01d9ed2068b42ff90",
                "MacAddress": "02:42:ac:11:00:04",
                "IPv4Address": "172.17.0.4/16",
                "IPv6Address": ""
```


