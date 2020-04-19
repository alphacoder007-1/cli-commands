Docker Basic Commands Example
===================================

### Clone the following project 

	git clone https://github.com/docker/doodle.git

### BUILD 

	cd doodle\cheers2019 ; 
	docker build -t alphacoder007/cheers2019 .

### RUN 

	docker run -it --rm alphacoder007/cheers2019


### SHIP

	docker login ; 
	docker push alphacoder007/cheers2019


Docker Image Commands 
========================

### Version of the doker installed

	Docker -v

### List all the images

	docker images

	docker image list

### Pull down the image

	docker pull [image-name] 

### Remove images

	docker rmi [imagename/imageid] 

### Build image

	docker build -t [imagename] . 

- **-t** tags as image
- **.** dot represents current directory

Docker Containers Commands 
===========================

### Run the docker images in a container (Option 1)

	docker run -it [image-name] [container-name]  

### Run the docker images in a container (Option 2)

	docker run -it --rm -p 5000:80 --name [container-name] [image-name] 

- **-it** flag will take all the ouput from the container and pipe it to console window
- **--rm** will remove the intermediary build
- **-p** will map the port 80 from the container to port 5000 on local machine  

### List all the containers running
	
	docker ps

	docker container list

### Stop the running container
	
	docker stop [container-name/container-id]
	
### List all the containers available

	docker ps -a
	docker container list -a

### delete the container 

	docker container rm [container-name/container-id]

### Remove all build cache, stopped containers and dangling images 

	docker system prune

Docker for SQL Server 
=====================================

### Pull the sql server 2019 image

	docker pull mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu

### Docker command for SQL Server image (Option 1)

	docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Docker@1' -e 'MSSQL_PID=express' -p 1445:1433 --name=moviesdb microsoft/mssql-server-linux:latest

- Provide _localhost,1445_ as server name when you open SSMS
- Provide Login as _sa_
- Provide password as  _Docker@1_

### Docker command for SQL Server image (Option 2)

	docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=Docker@1" -p 1433:1433 --name sql1 -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu

- -e "ACCEPT_EULA=Y" - 	acceptance of the End-User Licensing Agreement
- -e "SA_PASSWORD=<YourStrong@Passw0rd\>" -	The password should follow the SQL Server default password policy
- -p 1433:1433 -	Map a TCP port on the host environment (first value) with a TCP port in the container (second value). 
					In this example, SQL Server is listening on TCP 1433 in the container and this is exposed to the port, 1433, on the host.
- --name sql1 -	Specify a custom name for the container rather than a randomly generated one. If you run more than one container, you cannot reuse this same name.
- mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu -	The SQL Server 2019 CTP3.2 Linux container image.

### Connecting to SQL Server via command line

	docker exec -it moviesdb /opt/mssql-tools/bin/sqlcmd -S localhost -U sa

- -s means server
- -u means user

	docker exec -it sql1 "bash"

	/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<YourNewStrong@Passw0rd>"

### Create and query data

	CREATE DATABASE TestDB
	SELECT Name from sys.Databases
	GO

### Insert Data

	USE TestDB
	CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
	INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
	GO

### Select data

	SELECT * FROM Inventory WHERE quantity > 152;
	GO

### Exit the sqlcmd command prompt

	QUIT

- To exit the interactive command-prompt in your container, type exit. Your container continues to run after you exit the interactive bash shell.

### Connect from outside the container

	sqlcmd -S <ip_address>,1433 -U SA -P "<YourNewStrong@Passw0rd>"

### Remove your container

	docker stop sql1

	docker rm sql1


Docker Compose Commands
==============================

### Run the docker compose file
	
	docker-compose up
	
### Bring down the docker compose file
	
	docker-compose down
	
### build the docker compose file
	
	docker-compose build


Pushing Image to docker hub
=================================

### First we need to tag the image with our username 

	docker tag [imageid] [username]/[imagename]:[tag-name]

### Secondly, We need to login  

	docker login

### And finally we need to push 

	docker push [username]/[imagename]:[tag-name]


Docker Cli Commands from Dot Net Karma
============================================
### Docker version
	docker --version

### List all containers
	docker ps -a
 
### MS-SQL Container Running
	docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<Strong@Pwd>' -e 'MSSQL_PID=Express' -p 1433:1433 --rm -d mcr.microsoft.com/mssql/server:latest

### MS SQL Container RUN with name and Volume (Ubuntu)

	docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Purple1!' -e 'MSSQL_PID=Express' -p 1433:1433 --name mssql -v sqlvolume:/var/opt/mssql  --rm -d mcr.microsoft.com/mssql/server:latest	

### MS SQL Container RUN with name and Volume (Windows)

	docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Purple1!' -e 'MSSQL_PID=Express' -p 1433:1433 --name mssql -v C:/docker/sqldb:/var/opt/mssql  --rm -d mcr.microsoft.com/mssql/server:latest

### MS-sql-server EF Code first database update via vs code

	dotnet ef database update --verbose

### Datasource name for connecting to MS-SQL Server(outside container) from app running inside container

	host.docker.internal,1433

### INSPECT - Find IP address of the Running container

	docker inspect -f "{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}" <ContainerID | ContainerName>

- Required to connect to sql server from dotnet code


### Docker Network list

	docker network ls

- there are four types of network drives (bridge, host, overlay, null)
- bridge - 
- host - host are independent and each containers are disconnected
- overlay - multiple machines and multiple containers communicate each other
- null - no networking , simlpe conatainer and deploy ina single container

### Creating bridge network

	 docker network create --driver bridge mynetwork

### Network Inspect

	docker network inspect mynetwork

### Connecting and Changing container network

	docker network connect mynetwork <ContainerID | ContainerName>

### Disconnecting the container from network

	docker network disconnect mynetwork <ContainerID | ContainerName>

Docker Service (Docker Swarm)
===============================

### Intialise the docker swarm part of orchestration

	docker swarm init

### List docker services

	docker service ls

### Build image using -f flag

	docker build -t alphacoder007/fairview:5.0 . -f <Dockerfilepath>

- -f is for docker filename path

### Creating docker service

	docker service create --publish 5015:80 --name fairviewservice alphacoder007/fairview:5.0


### Scale up Docker Service

	docker service scale fairviewservice=3

- this create 3 replicas of the container 

### Scale down docker service

	docker service scale fairviewservice=1


Kubernetes
===============================================
### Verify Version

	kubectl version

### Deploy Dashboard GUI

	kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/alternative/kubernetes-dashboard.yaml

### Access Dashboard using the kubectl command-line tool

	kubectl proxy

### Access Dashboard
	
	http://localhost:8001/api/v1/namespaces/kube-system/services/http:kubernetes-dashboard:/proxy/#!/overview?namespace=default
k
### Create deployment

	kubectl apply -f .\deployment.yml

### List Deployments

	kubectl get deployments

### List of Nodes

	kubectl get nodes

### Lsit of Pods

	kubectl get pods

### Creating Service

	kubectl apply -f .\service.yml

### List Services

	kubectl get service

### Delete Deployments 
	kubectl delete deployments kdmvc

### Delete Service
	kubectl delete service kdmvc-service










 
