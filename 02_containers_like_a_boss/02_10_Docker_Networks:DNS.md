# Docker Networks : DNS and How containers find each other

- Understand how DNS is the key to easy inter-container comms
- See how it works by default with custom networks
- Learn how to use --link to enable DNS on default bridge network

## Docker DNS
Docker daemon has a built-in DNS server that contaienrs us by default

## Docker Default Names
Docker defaults the hostname to the container's name, but you can also set aliases. 
<mark>Note: </mark> This is what solves a huge problem when you're spinning up containers because you can't predict how long they're going to last and where they might be a minute from now. Also IP of containers keep changing when they're restarted. 

