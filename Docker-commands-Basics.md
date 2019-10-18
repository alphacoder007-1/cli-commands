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

	docker image list

### List all images

	docker images

### Pull down the image

	docker pull [image name] 

### Remove images

	docker rmi imagename/image_id 

### Build image

	docker build -t [App-ImageName] . 

- -t tags as image
- . means current directory

Docker Containers Commands 
===========================

### Run the docker images in a container

	docker run -it [image-name] [container-name] 

### Spinning Container from Image

	docker run -it --rm -p 5000:80 --name [Container-Name] [Image-Name]

- -it flag will take all the ouput from the container and pipe it to console window
- --rm will remove the intermediary build
- -p will map the port 80 from the container to port 5000 on local machine  

### List all the containers running
	
	docker container list

### List all the running containers

	docker ps

### Stop the running container
	
	docker stop [Container-name/Container-id]
	
### List all the containers available

	docker container list -a

### delete the container 

	docker container rm [Container-Name/Container-id]

### Remove all build cache, stopped containers and dangling images 

	docker system prune

Docker for SQL Server 
=====================================

### Docker command for SQL Server image 

	docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Docker@1' -e 'MSSQL_PID=express' -p 1445:1433 --name=moviesdb microsoft/mssql-server-linux:latest

- Provide _localhost,1445_ as server name when you open SSMS
- Provide Login as _sa_
- Provide password as  _Docker@1_

### Connecting to SQL Server via command line

	docker exec -it moviesdb /opt/mssql-tools/bin/sqlcmd -S localhost -U sa

- -s means server
- -u means user







 