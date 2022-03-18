# docker-cheatsheet


## Task 1:

  Get mysql:8 image and specify ports, volumes and docker version
  by which the image is built.
  
  ### Answer:
    docker pull mysql:8
  
    docker inspect 

## Task 2:

  1. Get nginx:latest image and save it to a local file. then load it using
    load and import commands.
    
   ### Answer:
    docker pull nginx:latest
    docker save nginx:latest -o nginx.tar
    docker load -i nginx.tar    
    docker import nginx.tar nginx:2
  2. explain differences between LOAD and IMPORT commands
  
   ### Answer:
 LOAD command loads the image with no changes while IMPORT merges all
 the layers, erases all the history and metadata of the image.
## Task3:
  Run a nginx container and bind it to port 8081 of the host.
  ### Answer:
    docker run -p 8081:80 nginx
## Task4: 
  Find the number of running processes of the container run in the previous task.
  ### Answer:
    docker top nginx | nl
## Task5: 
   Run an alpine container and install nginx on it, then make a docker image out of it.
   ### Answer:
     docker run --rm -it --name alpine alpine
  In the container:
  
     apk add nginx
  In the host:
  
     docker commit alpine alpine:nginx
## Task6:  
   Run a redis container then write it's id in a file named myredis.cid
   ### Answer:
     docker run --rm -it --name redis redis
     docker container inspect alpine  | jq '.[0].Id' > myredis.cid
## Task7:
   Run a nginx container which is limited to CPU=1.5core, Memory=512M and Swap=256M.
   Also the container's processes must only be run on cores number 0 and 2.
   ### Answer:
    docker run --rm -it --name nginx --memory=512m --memory-swap=768m --cpus="1.5" --cpuset-cpus=0,2 nginx:latest
 Note: --memory-swap = maximum_memory + maximum_swap 
## Task8:
   Run an alpine container and set CLASS=dws and NAME=saeed as enviroment variables in the container.
   Then in the container, display these two enviroment variables.
   ### Answer:
    docker run --name alpine -it -e CLASS=dws -e NAME=saeed alpine
    echo $NAME & echo $CLASS

     
