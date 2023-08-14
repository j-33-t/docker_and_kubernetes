Docker commands 

- docker run <image-name> : this commands run the image using docker cli
  
```docker run = "docker create" + "docker start" ```

- docker ps : shows all running containers
- docker ps --all : shows history of executed containers
- docker system prune : deletes all stopped containers, networks not used, dangling images, build cache from docker hub

- docker stop <container-id> : this stops the running container

- docker kill <container-id> : this kills the running container

- docker exec -it <container-id> <command> : execute an additional command in a container

- docker exec -it <container-id> sh : this will open up the command prompt/terminal.

purpose of the "-it" flag : in reality the it flag is two flags -i and -t , -i here directs to attach command to stdin in linux env and -t here directs stdout and stderr in the linux environment.  

- control + c to stop the command prompt , to exit container control + d


- command processors =   bash,powershell, zsh, sh , for docker containers you will most likely use sh


- docker run -it <container-id> sh : will start up the shell  immediately but will prevent other commands from executing in this container.

- 
