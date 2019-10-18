Docker Basics Commands Example
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

### List all the containers running
	
	docker container list

### Stop the running container
	
	docker stop [Container-name/Container-id]
	
### List all the containers available

	docker container list -a

### delete the container 

	docker container rm [Container-Name/Container-id]



 