# Assignment : Named Volumes

- Database upgrade with containers
- Create a ```postgres``` container with named volume psql-data using version ```9.6.1```
- Use Docker Hub to learn ```VOLUME``` path and versions needed to run it
- Check logs, stop container
- Create new ```postgres``` container with same named volume (i.e psql-data) using ```9.6.2```
- Check logs to validate


# Solution 

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
