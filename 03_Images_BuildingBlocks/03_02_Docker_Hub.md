# This lecture
- Basics of Docker Hub 
- Find Official and other good public images
- Download images and basics of image tags


# Images and their Layers : Discover the image cache
- ```docker image history <image-name>``` : Show layers of changes made in images
- ```docker image inspect <image-name>``` : Returns JSON metadata about the image


- Images are made up of file system changes and metadata
- Each layer is uniquely identified and only stored once on a host
- This saves storage space on host and transfer time on push/pull
- A container is just a single read/write layer on top of image


# Image tagging and Pushing to Docker Hub
- All about image tags
- How to upload to docker hub
- Image ID vs Tag

- ```docker image tag``` : assign one  or more tags to an image, default tag is latest if not specified ( ```<user>/<repo>:<tag>```)


In Docker, a "tag" is a label or identifier that you can assign to a specific version or variant of a Docker image. Tags are used to differentiate between different versions of the same image. Images with the same name but different tags are treated as distinct images by Docker.

- ```docer image push <image-name>``` : uploads changed layers to a image registry (default is Hub)
