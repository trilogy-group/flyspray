# Dockerfile

Dockefile is created on top of `php:5-apache-jessie` image.

# Requirements
- The project should be cloned from https://github.com/trilogy-group/flyspray
- Docker version 18.06.0-ce
- Docker compose version 1.22.0

# Quick Start

- Unzip `flyspray-Docker.zip` in `flyspray` directory
- Open a terminal session to that folder
- Clone the repository by running `git clone https://github.com/trilogy-group/flyspray.git`
- Run `docker-compose build`
- Run `docker-compose up -d`
- Run `docker exec -it flyspray bash`
- At this point you must be inside the docker container, in the root folder of the project. From there, you need to install few dependencies:
	- Run `curl -sS https://getcomposer.org/installer | php` 
	- `php composer.phar install`
	- To access running instance, navigate to 'http://localhost'
- When you finish working with the container, type `exit`
- Run `docker-compose down` to stop the service.

## Configuring Flyspray
When you run the application first time, it will require some inputs from you. Make sure the container has write access to `flyspray/flyspray` folder as well as to provide correct database parameters (which can be found under `flyspray/docker-compose.yml` file. 

## Build the image

In `flyspray` folder, run:

```bash
docker-compose build
```

This instruction will create a docker image in your machine called `flyspray_builder:latest`

## Run the container

In `flyspray` folder, run:

```bash
docker-compose up -d
```

Parameter `-d` makes the container run in detached mode.
This command will create a running container in detached mode called `flyspray`.
You can check the containers running with `docker ps`

## Get a container session

Run:

```bash
docker exec -it flyspray bash
```

Parameters `-it` allocate an interactive TTY session

## docker-compose.yml

The docker-compose.yml file contains both MySQL instance and a service called `builder`, which is used to run the application. 
We will use this service to run flyspray from our local environment, so we mount root project dir `./flyspray` to the a `/var/www/html/` folder:

```yaml
    volumes:
      - ./flyspray/:/var/www/html/:Z
```

## Requirements
The container was tested successfully on:
- Docker 17.05 and up
- docker-compose 1.8 and up

