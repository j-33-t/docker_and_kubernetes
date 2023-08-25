# This shows how we can extend/change official image from docker hub
FROM nginx:latest

# Change working directory to root of nginx webhost
WORKDIR /usr/share/nginx/html

# Copying hello world index.html
COPY index.html index.html

# I don't have to specify EXPORE or CMD because it exsits already in the this FROM image
