# Assignment 1 : Named Volumes

- Database upgrade with containers
- Create a ```postgres``` container with named volume psql-data using version ```9.6.1```
- Use Docker Hub to learn ```VOLUME``` path and versions needed to run it
- Check logs, stop container
- Create new ```postgres``` container with same named volume (i.e psql-data) using ```9.6.2```
- Check logs to validate


## Solution 

Create volume
```docker volume create psql-data```

Run container 
```docker run -d --name psql-1 -e POSTGRES_PASSWORD=mypassword -v psql:/var/lib/postgresql/data postgres:9.6.1```

Check logs 
```docker logs psql-1```

Run container with another version 
```docker run -d --name psql-2 -e POSTGRES_PASSWORD=mypassword -v psql:/var/lib/postgresql/data postgres:9.6.2```

Check logs 
```docker logs psql-2```

# Assignment 2 : Bind Mounts
- Use a Jekyll "static site generator" to start a local web server
- Disclaimer : One doesn't have to be a web developer: this is example of bridging the gap between local file acces and apps running in containers
- source code at "/04_practice/bindmount-sample-1"
- We edit files with editor on our host using native tools
- Container detects changes with host files and updates web server
- Start container with 
```docker run -p 80:4000 -v $(pwd):/site bretfisher/jekyll-serve```
- Refresh our browser to see changes
- Change the file in ```_posts\``` and refresh browser to see changes. 


## Solution 
