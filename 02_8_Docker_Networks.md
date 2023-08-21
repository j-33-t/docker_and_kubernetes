# Docker Networks : Concepts
- review of ```docker container run -p```
- For local dev/testing, networks usually "just work"
- Quick port check with ```docker container port <container>```
- Learn concepts of Docker Networking
- Understand how network packets move around Docker


## Docker Networks Defaults 
- Each container connected to a private virtual network "bridge"
- Each virtual network routes through NAT firewall on host IP
- All containers on a virtual network can talk to each other without -p
- Best practices is to create a new virtual network for each app:
    - network "my_web_app" for mysql and php/apache containers
    - network "my_api" for mongo and nodejs containers



## Commands
1. ```-p``` or ```-publish``` : is publishing ports in HOST:CONTAINER format
2. ```docker container port <container-name>``` : This ommand is used to display the public-facing port that a container's port is mapped to on the host system.
3. ```docker container inspect --format '{{.NetworkSettings.IPAddress}}``` : A common option for formatting the output of commands using "GO templates"
4. ```ifconfig | grep "inet " | grep -v 127.0.0.1 | awk '{print $2}'``` : print my ip for macOS

Running command 3 and 4 it can be observed that IP address is not same for docker container and host/macOS

```mermaid


```

Inside the Docker container, there's a "Virtual NIC" (Network Interface Card) that connects to the container's IP address (e.g., a private IP assigned by Docker).
On your macOS computer, the application connects to the macOS Kernel, which, in turn, communicates with the physical NIC and your computer's IP address (e.g., your computer's local or public IP).