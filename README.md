# Docker Cheat Sheet

To show list of machine

	$ docker-machine ls
	
To start docker machine

	$ docker-machine start <name>
	Starting VM...

To stop docker machine

	$ docker-machine stop <name>
	
## Docker Images

To show list of images

	$ docker images

To delete image

	$ docker rmi <images id>
	
To delete all images

	$ docker rmi $(docker images -q)