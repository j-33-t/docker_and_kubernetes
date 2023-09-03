# Docker Swarm init: What just happened ?

**command :**

```docker swarm init```

**output :**

```Swarm initialized: current node (79dwc3dy9pp621pbdqqszha37) is now a manager.```

```To add a worker to this swarm, run the following command: docker swarm join --token SWMTKN-1-50xbky88saf23wdm7e2g0ouugwbs7axpofak0fhti3gr994t3t-33j284i5phpm13sp5gulbk5sr 192.168.65.3:23```

## Lots of PKI and security automation
- Root signing certificate created for our swarm
- Certificate is issued for first Manager mode
- Join tokens are created

## Raft database created to store root CA, configs and secrets
- Encrypted by default on disk (1.13+)
- Non need for another key/value system to hold orchestration/secrets
- Replicates logs amongst Managers via mutual TLS in "control plane"
