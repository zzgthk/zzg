% zhuzhenguang
% 2017-01-03

## Docker Introduction

https://www.docker.com/what-docker


## Some Concepts

Image: An image is an ordered collection of root filesystem changes and the con the corresponding execution parameters for use within a container runtime. Images are read-only.
    https://docs.docker.com/engine/reference/glossary/#image

Container: A container is an active (or inactive if exited) stateful instantiation of an image.
    https://docs.docker.com/engine/reference/glossary/#container

## Install Docker in Ubuntu 14.04

[Install Docker on Ubuntu](https://docs.docker.com/engine/installation/linux/ubuntulinux/)

sudo apt-get update

sudo apt-get install apt-transport-https ca-certificates

sudo apt-key adv \
            --keyserver hkp://ha.pool.sks-keyservers.net:80 \
            --recv-keys 58118E89F3A912897C070ADBF76221572C52609D


echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" | sudo tee /etc/apt/sources.list.d/docker.list


sudo apt-get update

// For Ubuntu Trusty, Wily, and Xenial, install the linux-image-extra-* kernel packages, which allows you use the aufs storage driver.

sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual


sudo apt-get install docker-engine

// start the docker service or deamon

sudo service docker start

// set user group for no need to sudo every time

sudo groupadd docker

sudo usermod -aG docker $USER

## A simple Example

docker run -ti --name test ubuntu:14.04 /bin/bash

if network not work, you can use the host:

docker run --net=host --name test -i -t ubuntu:14.04 /bin/bash

## mapping a port to container

docker run -ti -p local_host_port:container_port --name test_port ubuntu:14.04 /bin/bash

// after enter the container

sudo apt-get update && sudo apt-get install python && python -m SimpleHTTPServer 8080

// then test it from host

curl localhost:8000

### detach & attach container

detach from a container:  ctrl + p + q

attatch a container:  docker attach ID/NAME


### start & stop a container

docker stop|start|restart ID

stop all containers:   docker kill $(sudo docker ps -q)

### create & delete operation

delete a container:   docker rm ID/NAME

delete all containers:  docker rm $(docker ps -q)

delete a image:  docker rmi ID

list all images installed:  docker images

create a new image from modifed one:  docker commit -m "xxx" image_name

setting tags on an image:  docker tag ID author_namae/image_name:tag_name

### copy file operations

docker run -tid -v host_abs_path:container_abs_path --name your_container_name image_name command

docker run -tid -v /home/zzg/repo:/home/share_test --name share_test ubuntu:14.04 /bin/bash

### stats information command

how many containers are there in docker:   docker ps

only show the id: docker ps -q

to see how many resources are used by containers:  docker stats

look docker log:   docker ps -a

look a container log:  docker logs ID/NAME

look a container configure:  docker inspect ID

network : docker network ls

