## Section Overview
- Defining the problem of persistent data
- Key concetps with containers: immutable, ephemeral 
- Learning and using Data Volumes
- Learning ans using Bind Mounts
- Assignments


## Container Lifetime and Persistent Data
- Container are usually immutable and ephemeral (i.e unchanging and temporary, or disposable)
- "immutable infrastructure": only re-deploy containers, never change
- This is the ideal scenario, but what about databases, or unique data?
- Docker gives us features to ensure these "separation of concerns"
- this is known as "persistent data"
- Two ways : **"Volumes"** and **"Bind Mounts"**
- Volumes : make special location outside of container UFS (union file system)
- Bind Mounts : link container path to host path, which is us sharing or mounting a host directory or file into a container. It will look like  local file path or directory path to container. It won't actually know that it's coming from the host. 


## Persistent Data : Bind Mounting
- Maps a host file or directory to a container file or directory
- Basically just two locations pointing to the same file(s)
- Again, skips UFS, and host files overwrite any in container
- Can't use in Dockerfile, must be at  ```container run```
- ```....run -v /Users/bret/stuff:/path/container``` (mac/linux)
- ```....run -v //c/Users/bret/stuff:path/container``` (windows)



# Practice 

First start container with ngnix and map the file to current working directory (i.e "04_Persistent_Data/04_practice/dockerfile-sample-2")
```docker container run -d --name ngnix -p 80:80 -v $(pwd):/usr/share/nginx/html nginx```

Open browser and check if browser is running at ```"localhost:80"```


Open container shell and go to directory "/usr/share/nginx/html"
```cd /usr/share/nginx/html```

List the files (command will show Dockerfile , index.html)
```ls```

Create another file on local computer in current working directory (i.e "04_Persistent_Data/04_practice/dockerfile-sample-2")

mac/linux command
```touch testing.txt```

This file also now exists in container at "/usr/share/nginx/html"

write something in the testing.txt document 
```echo "testing 1.2.3" > testing.txt``` 

check file output in browser
```localhost:testing.txt```
