# Building Images : Dockerfile Basics

Dockerfile is file which stores the recipe of creating images

It is critically important on how to order things in dockerfile. 
Usually things at the top are things that will not change. 
Since docker uses cache and runs everything after the changed line. 
The things that change the most should be at the bottom of your dockerfile. 

- the ```-f``` command is used to specify a dockerfile, which an alias of --file, this is only to be used when referecing a file other than default 'Dockerfile'


# Practice

## Test the default nginx webpage in browser

*running test container (--rm will remove the conatiner on exit)*
```docker container run -p 80:80 --rm nginx```

## Run custom html file using nginx (03_Exercises/Build_Demo)
*open new terminal and specify directory in terminal*

```cd 03_Exercises/Build_Demo```
*now build image*
```docker image build -t nginx-html .```

*now run the new image *
```docker container run -p 80:80 --rm nginx-html```
