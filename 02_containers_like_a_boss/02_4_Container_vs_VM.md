# Containers aren't Mini-VM's

- They are just processes
- Limited to what resources they can access
- Exit when process stops

# Commands

Example:
- docker run --name mongo -d mongo
- docker ps
- docker top mongo

1. Listing all processes running inside a container using : ```docker top <container-name>```


Containers are really just restritcted processes running on the OS kernel. The executable files in those containers have to be built for the kernel they are running on. This is why Docker Desktop uses a lightweight LINUX VM to run your containers. 