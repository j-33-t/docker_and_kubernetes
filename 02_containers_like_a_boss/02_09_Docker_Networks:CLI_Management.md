# Docker Networks : CLI Managemenet
1. Show networks : ```docker network ls```
2. Inspect network : ```docker network inspect <network name>```
3. Create a network : ```docker network create <network name>```
4. Attach a network: ```docker network connect```
5. Detach a network from container: ```docker network disconnect```
6. Remove a network : ```docker network rm <network name>```

## Example of attaching network to container
```docker container run --name mynginx --network mynetwork --detach nginx```

# Docker Networks : Default Security
1. Create your apps so frontend/backend sit on same Docker network
2. Their inter-communication never leaves host
3. All externally exposed ports closed by default
4. You must manually expose via -p, which is better default security!
5. This gets even better later with Swarm and Overlay networks