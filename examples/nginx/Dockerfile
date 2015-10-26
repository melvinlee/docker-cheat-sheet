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