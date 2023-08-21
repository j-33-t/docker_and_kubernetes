# Assignment : DNS Round Robin Test

## Requirements
- Know how to use ```-it``` to get shell in container
- Understand basics of what a Linux distribution is like Ubuntu and CentOS
- Know how to run a container
- Understand basics of DNS records

# Basics Of DNS Records

DNS (Domain Name System) records are essential components of the internet infrastructure that translate human-readable domain names (like www.example.com) into machine-readable IP addresses (such as 192.0.2.1). They play a critical role in allowing users to access websites and services using familiar domain names instead of numerical IP addresses.

Here are some of the basic types of DNS records and their purposes:

1. A Record (Address Record): <br>
An A record associates a domain name with an IPv4 address. It is used to point a domain directly to an IP address. For example, if you have an A record for "www.example.com" with the IP address "192.0.2.1," anyone typing "www.example.com" in their web browser will be directed to that IP address.

2. AAAA Record: <br>
Similar to the A record, the AAAA record associates a domain name with an IPv6 address. As the internet transitions to IPv6 due to the depletion of available IPv4 addresses, AAAA records become more important for addressing.

3. CNAME Record (Canonical Name Record): <br>
A CNAME record creates an alias for a domain name. Instead of pointing directly to an IP address, it points to another domain name. This is useful when you want multiple domain names to point to the same IP address. For instance, you could create a CNAME record for "blog.example.com" that points to "www.example.com."

4. MX Record (Mail Exchange Record): <br>
MX records are used to direct email messages to the appropriate mail server for a domain. They specify the mail server's domain name and priority (lower values indicate higher priority). This ensures that email sent to addresses like "user@example.com" reaches the correct mail server.

5. TXT Record (Text Record): <br>
TXT records are used to store text-based information about a domain. They have various uses, including domain verification for services like email authentication (SPF, DKIM), human-readable notes, and more.

6. SRV Record (Service Record): <br>
SRV records define the location of a specific service within a domain. They are commonly used for services like instant messaging, Voice over IP (VoIP), and other network-related services. An SRV record includes details such as the service's protocol, domain name, port number, and priority.

7. NS Record (Name Server Record):<br>
 NS records specify the authoritative name servers for a domain. These name servers hold information about the domain's DNS records. When someone looks up a domain's DNS information, they query the name servers specified in the NS records.

8. PTR Record (Pointer Record): <br>
PTR records perform the reverse of what A and AAAA records do. Instead of translating a domain name to an IP address, they translate an IP address back to a domain name. PTR records are commonly used for reverse DNS lookups, which help identify the domain associated with an IP address.

These are some of the fundamental DNS record types, each serving a specific purpose in the DNS system. DNS records are managed by domain registrars, web hosting providers, and DNS hosting services. Properly configuring and managing DNS records is crucial for ensuring the smooth functioning of websites and online services.

# Assignment : DNS Round Robin Test
*DNS round-robin testing is a simple load balancing technique used to distribute incoming network traffic across multiple servers or resources.*

- Ever since Docker Engine 1.11, we can have multiple containers on a created network respond to the same DNS address. 
- Create a new virtual network (default bridge driver)
- Create two new containers from ```elasticsearch:2``` image
- Research and use ```-network-alias search``` when creating them to give them an additional DNS name to respond to
- Run ```alpine nslookup search``` with ```--net``` to see the two containers list for the same DNS name. 
- Run ```centos curl -s search:9200``` with ```--net``` multiple times until you see both "name" fields show

# Solution 
```
docker network create dude
```

Run the below command twice to create 2 containers
```
docker container run --network dude --network-alias search -detach elasticsearch:2
```

```
docker container run --rm --network dude alpine nslookup search
```

```
docker container run --rm --network dude centos:7 curl -s search:9200
```

for same output as centos in alpine use command below
```
docker container run --rm --network dude alpine sh -c "apk add --no-cache curl && curl -s search:9200"
```