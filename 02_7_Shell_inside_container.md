# Getting a Shell Inside Container
- docker container run -it : start new container interactively
- docker container exec -it : run additional command in existing container
- different linux distros in containers

There is no need for SSH for container to access shell inside container

"docker container run <mark>-it</mark>"
- "-it" is acutally two commands:
    1. t = Allocate a psuedo-TTY (It simulates a real terminal, like what SSH does)
    2. i = interactive (Keep session open to receive terminal input)


## Example Commands:

### Run container with bash
```docker container run -it --name mynginx nginx bash```

#### Restart container 

```docker container start -ai mynginx```

    - "-ai" : where a is attach and i is interactive

#### Exec container

```docker container exec -it mynginx bash```
docker exec command is used to run a command inside a running container. It allows you to interact with a container that's already running, without the need to start a new shell session in the container. 

