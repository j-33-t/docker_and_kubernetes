# Docker Compose:
- Why: configure relationships between containers
- Why: save our docker container run settings in easy-to-read file
- Why: create one-liner developer environmnet startups
- Comprised of 2 separate but related things:<br>
    1. YAML:<br>
        yaml-formatted file that descibes out solution options for:<br>
            - containers <br>
            - networks  <br>
            - volumes

    2. A CLI tool ```docker-compose``` used for local dev/test automation with those YAML files


## docker-compose.yml
- Compose YAML format has it's own versions: 1,2,2.1,3,3.1
- YAML file can be used with ```docker-compose ``` command for local docker automation
- with ```docker``` directly in production with Swarm (as of v1.13)
- help with ```docker-compose --help```
- ```docker-compose.yml``` is default filename, but any can be used with ```docker-compose -f <filename>```

