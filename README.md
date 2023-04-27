# Introduction - hadoop-docker

This is the candidate release for a docker based HADOOP setup with the following type of services:
 - namenode
 - datanode
 - nodemanager
 - resourcemanager 
 - historyserver

The docker based setup can be used in two scenarios:

- <b>docker-compose</b> setup <b>only for debugging</b>. In this scenario all containers are running on the same host but there is only one copy of the datanode service and hence no data replication, no multiprocessing, etc.
- <b>swarm based</b> - with services deployed on a swarm of docker nodes - each node running at least one datanode and nodemanager - while one of the nodes run the namenode and resourcemanager.

# Building
For building the whole project (docker images) from scratch, one needs to perform the following steps:

1. Go to the ***base*** folder and issue 
```bash
docker build [-t repo:tag] . 
cd ..
```
This will ensure you can directly push the resulting image to a docker image res=pository (like docker hub). 

2. Build the rest of the images by issuing:
```bash
docker compose build 
```
This will build all images accoring to the definitions in ***docker-compose.yml***

# Running the setup

1. Running in compose mode (for debugging) should be done by  issuing:
```bash
docker compuse up 
```
which will launch one instance of each container on the local machine. (the datanode can be scaled using "docker-composer scale node=x" but all datanodes will use the same storage volume which makes it useless and error prone). 
```bash
docker compose down 
```
do shutdown the setup.

2. Running in swarm mode requires a swarm already created with at least 3 nodes. 
<TBA>


  
This work was inspired by the https://github.com/big-data-europe/docker-hadoop project.
