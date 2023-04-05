# fetch ubuntu:20.04 image from docker hub
FROM ubuntu:20.04

# set the working directory to app
WORKDIR /usr/src/app

# copy script to container
COPY script.sh .

# chmod script
RUN chmod +x script.sh

# install curl
RUN apt-get update && apt-get install -y curl

# run script
CMD ./script.sh