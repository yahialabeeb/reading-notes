# Docker
## Overview 
* it is just Linux containers which are a type of virtualization.
* with Docker The entire development environment is isolated 
* Docker we now longer have to mess around with virtual environments
* Docker can be shared among team members so everyone is working on the same setup
* virtual machines which are complete copies of a computer system from the operating system on up to allow multiple programmers use the same single machine. 

## Linux Containers
* Docker is really just Linux containers which are a type of virtualization. 

* Containerization has become increasingly popular becouse it provides a lightweight, faster way to duplicate much of the same functionality.

## Containers vs Virtual Environments

* virtual environments can only isolate Python packages
* we can’t run a production database or other services within virtual

## Images and Containers

* create custom images using a Dockerfile.
* use docker-compose.yml files to run the containers.
* There are a large number of official images available on Docker Hub for common software 

## Images

1. create a local directory on your computer for code. 

2. Define the image with a Dockerfile. This is similar to a Pipenv, it is a list of all the requirements needed to build our image.

3. The first instruction must be the FROM command ```FROM python:3.7-alpine``` which lets us import a base image to use for our images. This base image could be another Docker image or one we create entirely from scratch.

## Image Builds
``` docker image build . ```it’s time to “build” or create the image 

* We can list all existing Docker images to confirm this new one has been built alongside the initial alpine image.

## Image Layers
Every image is made up of one or more image layers.

* called image layering is image depended on other images and it exists for two main reasons:
1. each image layer is immutable–unchanged–like a git commit. This helps ensure consistency when two developers build the same image. 
2. The second reason is performance. Docker caches the steps in a Dockerfile to speed up subsequent builds. When a change is made to a step, all steps following it will be executed from scratch.

## Containers
### docker-compose.yml file that is a list of container instructions.

* To demonstrate an image and container example we will now “Dockerize” a basic Django web app.

### Dockerized Django
* We’ll now create a Dockerfile for our image which will completely replace our local dev environment
* Then adding a docker-compose.yml for the container instructions. 
``` bash
$ touch Dockerfile
$ touch docker-compose.yml
```
This Dockerfile has several commands. RUN, COPY, and ADD each create a new layer.
 Dockerfile
``` bash
# Python version
FROM python:3.7-alpine

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Set work directory
WORKDIR /code

# Install dependencies
COPY Pipfile Pipfile.lock /code/
RUN pip install pipenv && pipenv install --system

# Copy project
COPY . /code/
```
* Order matters in Dockerfiles since they are executed from top-to-bottom.
 
1. we use FROM to install python:3.7-alpine as our base image and set two environment variables with ENV. 
    - The first, PYTHONDONTWRITEBYTECODE will remove .pyc files from our container which is a good optimization. 
    - The second, PYTHONUNBUFFERED will buffer our output so it will look “normal” within Docker for us.

2.  we used the WORKDIR command to create and set /code as our default directory within Docker. 

3. The Pipfile contains information on our software packages so we copy that over, too.

4.  we install Pipenv itself via pip and then run pipenv install to install the software packages in our Pipfile. *Note that we added the --system tag so that software packages are available throughout the entire container, not within a virtual environment which is Pipenv’s default but doesn’t make sense here since the entire Docker container is a virtual environment.*


An important point to make here is that the order in a Dockerfile matters a lot. Because of layer caching when a step changes in the Dockerfile, all subsequent work needs to be redone.

For example, the very last line here is COPY . /code. That means any code changes locally will be copied over. However there are no commands after that; nothing else needs to be rebuilt. If we had put this command earlier in the Dockerfile, say, before we install the Pipfile, then every time there is a local code change all our requirements would have to be reinstalled on the image. Wasteful.

Without going too far down this rabbit hole, remember that order is extremely important for performance and managing image size.

Now time for docker-compose.yml.

# docker-compose.yml
version: '3.7'

services:
  web:
    build: .
    command: python /code/manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - 8000:8000
At the top we specify we’re using the 3.7 version of Docker Compose and then set up a service, which is running within our container.

Multiple services can run within a Docker host–for example, we might add a db service for a running PostgreSQL database in the future–but for now we have a single web service.

We tell it to build the current directory, execute runserver on startup which will start the Django server. Then volumes will sync our local directory to the Docker container. And as a final step we expose port 8000 which is Django’s default so the container will expose it, too.

Instead of running separate commands to build the image and run the container we can do that with one now. Check this out!


## Conclusion

* Docker is a way to run Linux containers
* Containers are a lightweight alternative to Virtual Machines
* Dockerfile is a list of instructions for creating an image
* Images are made up of one or more layers
* Containers are a running instance of an image
* docker-compose.yml controls how to run the container
* Containers are stateless and ephemeral in nature. 

[<= Back](read31.md)