# Setting up swarm on different systems

- Setup 3 linode machines running 3 different Linux OS (Debian, Ubuntu, Alpine)
- Change hostname using ```hostname <enter-name>```, name debian as node1, ubuntu as node2 and alpine as node3
- Install docker using (For debian and Ubuntu)
    - '```curl -fsSL https://get.docker.com -o install-docker.sh```'
    - '```sh install-docker.sh```'

- Install docker on alpine:
    - ```apk update```, ```apk add docker```

- For alpine linux add command to start docker on boot ```apk add --update docker openrc```

- perform swarm init on node1 (i.e Debian)
This will initialise a swarm and put this machine as leader 'role' and generate a token for other workers to join

- to add managers instead of workers to the swarm type ```docker swarm join-token manager```, this will generate a manager level token for the servers/nodes to join. 

- add node2 and node3 as manager using token generated from ```docker swarm join-token manager```

- check stats and manager status using ```docker node ls```

- deploy 3 conatiners using alpine image to ping 8.8.8.8 
    ```docker service create --replicas 3 alpine ping 8.8.8.8```

- check the running service by ```docker service ls```. Take the name of the conatiner from the output

- to see all deployed containers run ```docker service ps <service-name>```

*example*
```
root@localhost:~# docker service ps sleepy_brown
ID             NAME               IMAGE           NODE      DESIRED STATE   CURRENT STATE            
51230l62nv80   sleepy_brown.1   alpine:latest   node2     Running         Running 29 seconds ago             
3pduaxqzitu2   sleepy_brown.2   alpine:latest   node3     Running         Running 29 seconds ago             
fjha5xmy2m2l   sleepy_brown.3   alpine:latest   node1     Running         Running 30 seconds ago
```

### We now have a fully operational swarm cluster 🙂