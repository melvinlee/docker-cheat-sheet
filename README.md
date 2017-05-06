# Docker Cheat Sheet
## Quick-Start

To show list of docker machine

	$ docker-machine ls
	NAME      ACTIVE   DRIVER       STATE     URL                         SWARM
	default   *        virtualbox   Running   tcp://192.168.99.100:2376

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
	
