# Assignment: Create Multi-Service App

## Commands 
Start 2 machines/nodes running linux on linode, install docker on them using get.docker.com

Perform ```docker swarm init``` and ```docker swarm join-token manager``` to connect the 2 nodes by copying the docker swarm join token. 

check the status of the nodes created using 
```docker node ls```


1. On node 1, Creat backend network, Overlay is the only kind of network for swarm to span accross nodes
```bash
docker network create -d overlay backend
```
2. On node 2, Create Frontend network
```bash
docker network create -d overlay frontend
```

3. 
```bash
docker service create --name vote -p 80:80 --network frontend --replicas 2 dockersamples/examplevotingapp_vote:before
```

4. 
```bash
docker service create --name redis --network frontend --replicas 1 redis:3.2
```

5. 
```bash
docker service create --name worker --network frontend --network backend --replicas 1 dockersamples/examplevotingapp_worker
```

6. docker service has a different way to mount volume as compared to docker run -v, 
```bash
docker service create --name db --network backend -e POSTGRES_HOST_AUTH_METHOD=trust --mount type=volume,source=db-data,target=/var/lib/postgresql/data postgres:9.4
```

7. 
```bash
docker service create --name result --network backend -p 5001:80 bretfisher/examplevotingapp_result
```


check if services are running

```docker serivce ls```

check stats of one service
```docker service ps <service-name>```

check logs
```docker service logs```


## Checking final result

1. Find ip of the frontend network by 
```docker network inspect frontend```

2. Create shh tunnel between node2 and local machine
```ssh -L 5001:your-network-ip:80 user@your-server-ip```

3. open website by going to and vote on cat or dog ```http://your-network-up/```

4. check voting result by going to ```http://your-network-up:5001``