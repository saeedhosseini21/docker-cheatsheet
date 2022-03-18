################ docker-cheatsheet #############
Task 1:
  Get mysql:8 image and specify ports, volumes and docker version
  by which the image is built.
  Answer:
    docker pull mysql:8
    docker inspect 
Task 2:
  a)Get nginx:latest image and save it to a local file. then load it using
  load and import commands.
    Answer:
      docker pull nginx:latest
      docker save nginx:latest -o nginx.tar
      docker load -i nginx.tar
      docker import nginx.tar nginx:2
  
  b)explain differences between load and import commands
    Answer:
      load command loads the image with no changes while import merges all
      the layers, erases all the history and metadata of the image.
Task3:
  Run a nginx container and bind it to port 8081 of the host.
  Answer:
    docker run -p 8081:80 nginx
Task 4: 
  Find the number of running processes of the container run in the previous task.
  Answer:
    docker top nginx | nl
