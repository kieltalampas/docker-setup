# Docker Node.js Application

A simple Node.js application containerized with Docker.


## Project Structure

This project contains a simple Node.js application with the following structure:

```
project-root/
├── server.js          # Main application entry point
├── package.json       # Node.js dependencies and scripts
├── Dockerfile         # Instructions to build the Docker image
└── README.md          # This documentation
```

## Docker Setup

### Understanding the Dockerfile

Below is the Dockerfile with explanations for each instruction:

```dockerfile
# Start from the official Node.js image
FROM node

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json first for better caching
COPY package.json /app

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . /app

# The application listens on port 80
EXPOSE 80

# Command to run when the container starts
CMD ["node", "server.js"]


```
## Building Image and Running the Container


```dockerfile
# Navigate to the directory containing the Dockerfile
`cd /path/to/project`


# Build the image
`docker build .`

# Run the Container
`docker run -p 3000:80 <image id>`

#The command explained:
#- `docker run`: Creates and starts a new container
#- `-p 3000:80`: Maps port 3000 on your host to port 80 in the container
#- `<image id>`: The ID of the image you built in the previous step

```
## Stop the Container
```dockerfile
# List all running containers
`docker ps`

CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
a1b2c3d4e5f6   1f3e4b5c6d7e   "node server.js"         2 minutes ago    Up 2 minutes    0.0.0.0:3000->80/tcp   eloquent_hopper

# Stop the container using its name
`docker stop <container name>`


```
## Remove Container
```dockerfile
# Stop running Containers to remove
`docker rm <container name/s>`

# automatically remove container after being stop `--rm`
`docker run -p 3000:90 -d --rm <imageid>


```
## Remove Images
```dockerfile
# List all images
`docker images`

# Remove Images only if the container has been removed
`docker rmi <container name>

```
## Naming Containers
```dockerfile
# Build image
`docker build .`

# Run the container
`docker run -p 3000:80 -d --name <container name> <imageid>`


```
## Naming Images
```dockerfile
# Build image with -t
`docker build -t goals:latest .`


