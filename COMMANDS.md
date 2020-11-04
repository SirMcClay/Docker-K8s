# Some Docker commands

## docker build -t
Build an image based on the dockefile in the current directory.  
Tag it as 'stephengrider/posts'.  
*Ex.:* `docker build -t stephengrider/posts`

## docker run
Create and start a container based on the provided image id or tag.  
*Ex.:* `docker run [image id or image tag]`

## docker run -it \[image\] \[cmd\]
Create and start a container, but also override the default command.  
Tag it as 'stephengrider/posts'.  
*Ex.:* `docker run -it [image id or image tag] [cmd]`

## docker ps
Print out information about all of the running containers.  
*Ex.:* `docker ps`

## docker exec -it \[container\] \[cmd\]
Execute the given command in a running container.  
*Ex.:* `docker exec -it [container id] [cmd]`

## docker logs \[container\]
Print out logs from the given container.  
*Ex.:* `docker logs [container id]`

