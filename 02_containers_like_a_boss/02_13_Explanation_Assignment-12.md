# Explanation of Round Robin Test in 02_12

Let's break down the process step by step and explain the round robin DNS test being done using the provided commands.

**Step 1: Create a Docker Network**
```bash
docker network create dude
```
In the first step, a Docker network named "dude" is created. Docker networks are utilized for isolating containers and enabling communication between them using container names as hostnames.

**Step 2: Running Elasticsearch Containers**
```bash
docker container run --network dude --network-alias search -d elasticsearch:2
```
In the second step, Elasticsearch containers are launched and connected to the "dude" network. The flag `--network-alias` assigns the alias "search" to the containers, which can be used as a hostname within the Docker network.

**Step 3: Running CentOS Container with Curl**
```bash
docker container run --rm --network dude centos:7 curl -s search:9200
```
In this step, a CentOS container is started, linked to the "dude" network. The container executes a `curl` command to query the Elasticsearch instance using the hostname "search" and port 9200. Docker employs round-robin DNS resolution as there are two Elasticsearch containers (from the previous step), alternating between them.

**Explanation of Output for the First Run:**
```
{
  "name" : "Machinesmith",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "EhodLFsDRJ2IJMdXddtNUA",
  "version" : {
    "number" : "2.4.6",
    "build_hash" : "5376dca9f70f3abef96a77f4bb22720ace8240fd",
    "build_timestamp" : "2017-07-18T12:17:44Z",
    "build_snapshot" : false,
    "lucene_version" : "5.5.4"
  },
  "tagline" : "You Know, for Search"
}
```
The output provides information about the first Elasticsearch container reached during the initial round-robin DNS resolution. The "name" field denotes the name of the Elasticsearch instance ("Machinesmith"), and other fields offer details about the Elasticsearch version and build.

**Explanation of Output for the Second Run:**
```
{
  "name" : "Steel Spider",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "cebpsNKbQfuV772iYh6QXQ",
  "version" : {
    "number" : "2.4.6",
    "build_hash" : "5376dca9f70f3abef96a77f4bb22720ace8240fd",
    "build_timestamp" : "2017-07-18T12:17:44Z",
    "build_snapshot" : false,
    "lucene_version" : "5.5.4"
  },
  "tagline" : "You Know, for Search"
}
```
The output presents information about the second Elasticsearch container accessed during the subsequent round-robin DNS resolution. The "name" field signifies the name of the Elasticsearch instance ("Steel Spider").

**Purpose of Network Alias:**
A network alias serves to assign a recognizable hostname to a container within a Docker network. In this instance, the `--network-alias search` flag is utilized while initiating the Elasticsearch containers. This alias enables referring to the Elasticsearch instances with the hostname "search" within the Docker network. This simplifies container communication by offering a readable and static hostname.

Keep in mind that round-robin DNS resolution is based on the order of container initiation and may not uniformly distribute requests. It is a straightforward load-balancing approach that cycles through available instances.