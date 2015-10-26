# Docker Cheat Sheet

To show list of machine

	$ docker-machine ls
	
To start docker machine

	$ docker-machine start <name>
	Starting VM...

To stop docker machine

	$ docker-machine stop <name>
	
To configure your shell

	$ eval "$(docker-machine env default)"
	
## Docker Images

To show list of images

	$ docker images

To delete image

	$ docker rmi <images id>
	
To delete all images

	$ docker rmi $(docker images -q)
	
## Docker Build

*The **docker build** command builds an image from a Dockerfile and a context. The build’s context is the files at a specified location PATH or URL. The PATH is a directory on your local filesystem. The URL is a the location of a Git repository.*

- Create a directory with Dockerfile.

		$ mkdir docker-project
		$ cd docker-project
		$ touch Dockerfile
	
- Edit the Dockerfile.

		# Nginx
		
		FROM 	ubuntu:14.04
		
		RUN 	apt-get update
		# Install git, curl, nano and nginx
		RUN 	apt-get install -y git curl nano nginx
		# Create directory /apps
		RUN 	mkdir /apps
		# Copy all files from current folder to /apps/html
		ADD 	. /apps/html
		
		# Rename nginx.conf to ngnix.conf.original
		RUN     mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.original
		# Replace nginx.conf
		RUN     mv /apps/html/nginx.conf /etc/nginx/nginx.conf
		
		# Set working directory
		WORKDIR /apps/html
		
		# Listen on port 8888
		EXPOSE 	8888
		
		# Exec
		CMD 	nginx
 
- Run build

		$ docker build -t nginx .
		
## Docker Container

To show list of running container

	$ docker ps

To show list of all container

	$ docker ps -a

To delete container

	$ docker rm <container_id>
	
To delete all container

	$ docker rm $(docker ps -a -q)
	
To run new container with interactive mode

	$ docker run -i -t nginx /bin/bash
	
To run new container with daemon mode

	$ docker run -d -p 8888:8888 -t nginx
	
To stop running container

	$ docker stop <container_id>
	
To start container

	$ docker start <container_id>
	
## Bash / SSH

To bash into a running container

	$ docker exec -i -t <container_id> /bin/bash
	
