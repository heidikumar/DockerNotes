Docker Tips and Tricks
=======================

This file is a reference for some basic ideas and commands around Docker.

What are images and containers?
-------------------------------

Docker images are read-only files that are layered one on top of the other. An image can pull a previous image using a ‘From’ statement. Multiple FROM statements can be used technically, but Docker doesn’t advise this. Layered images pull in all the environmental specifications you need for your container. Docker images are static.

Docker containers are a thin, writable layer on top of the image. You can interact with containers, change files around, write new information, etc in a container. An example is running a container off a Postgres image and then saving the info in the database. That data will persist as long as the container is running.

Image related commands
-----------------------

Build an image called "imageName" from Dockerfile in current folder:
	docker build -t imageName .

Look at history of an image:
	docker history {{ImageID#}}

Container related commands
---------------------------

Run an image of a server:
	docker run -it -p 8080:8080 {{ImageID#}}

-it makes it run interactive
-p assigns ports, which is set up as VM_Port:Local_Machine_Port

Docker Compose
--------------

Docker compose is a useful way to build images and run containers all in one command. To run docker-compose, you must write a docker-compose.yml file. For more info, see Docker's Compose documentation : https://docs.docker.com/compose/compose-file/

Fun Stuff
---------

You can override the commands of the run by adding the desired command to the end of the run command.
For example:
	docker run -it -p 8080:8080 {{ImageID#}} echo hello world

Useful commands:
	docker ps : shows all currently running containers
	docker ps -a : shows all containers
	docker images : shows all loaded images
	docker rm [id] :  remove a container
	docker rmi : remove an image


