# Assignment: Using containers for CLI testing

## Assignment requirements : CLI App Testing
- Know how to use -it to get shell in container
- Understand basics of what a linux distribution is like Ubuntu/CentOS
- Know how to run a container

# Assignmnet : CLI App Testing 
- Use different Linux distro containers to check ```curl``` cli tool version
- Use two different terminal windows to start bash in both ```centos:7``` and ```ubuntu:14.04``` using ```-it```
- Learn the docker container ```--rm``` option so you can save cleanup
- Ensure curl is installed and on latest version for that distro
    - ubuntu : apt-get update && apt-get install curl
    - centos: yum update curl
- Check ```curl --version```

<mark>Note:</mark> In Docker, the ```--rm``` flag is used when running containers to automatically remove the container's filesystem and resources when the container exits. This can be particularly useful to clean up temporary containers or containers that are meant to be short-lived.