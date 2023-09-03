# Overlay Multi-Host Networking

- Just choose <mark>```--driver overlay```</mark> when creating network, this will createa a Swarm-wide bridge network where containers across hosts on the same virtual network can access each other kind of like they're on a VLAN. 

- Only for container-to-container traffic inside a single Swarm

- (optional)FUll networking encryption can also be enabled using IPiece SEC on network creation, it is off by default for performance reasons

- Each service can be connected to multiple networks

## Practice 

- ```docker network create --driver overlay mydrupal```
- ```docker network ls``` 
- ```docker service create --name psql --network mydrupal -e POSTGRES_PASSWORD=mypass postgres:14```
- ```docker service create --name drupal --network mydrupal -p 80:80 drupal:9```
