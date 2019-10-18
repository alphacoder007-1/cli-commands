Docker Commands from Docker website
====================================

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


Docker Commands Basics 
==========================

### Version of the doker installed

	Docker -v


### List all the images

	docker image list

### Pull down the image

	docker pull [image name] 

### Remove images

	docker rmi imagename/image_id 

 