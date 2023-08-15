# Specify a base iamge
From node:14-alpine


# Specifying working directory
WORKDIR /usr/app

# Copy everything from simplewebbapp directory to the container
Copy ./package.json ./ 

# Install some dependencies
RUN npm install

Copy ./ ./

# Default command 
CMD ["npm", "start"]
