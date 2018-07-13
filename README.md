# Lemp Docker Demo

A demo LEMP stack for Docker that works on Windows 10 HOME.

## Overview

This demo is a blank Laravel application which you can run and test out of the box using Docker.

## Laravel Environment Variables

### Database 

```dotenv
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=test_db
DB_USERNAME=root
DB_PASSWORD=secret
```

__Note:__ You will need to wait a few seconds or minutes before being able to run `php artisan migrate` commands from the app container. This is while mysql service is starting.

## Usage in a real development environment.

Copy and update the following files:

```
docker-compose.yml
app.docker
web.docker
vhost.conf
```

Then simply `docker-compose up -d` to build the containers.

### Accessing the app container

First check the app container's name by running:

```bash
docker ps
```

Assuming the container name is `lempdockerdemo_app_1` you can SSH into it:

```bash
docker exec -it lempdockerdemo_app_1 bash
```

From here you can run `artisan` command and other commands such as `phpunit`. However, as it is, you cannot run `composer` commands from within the container. You can however, either install `composer` in the container or run it from your host machine.

### Stopping all running containers

```bash
docker-composer kill
```

### Stop all Docker containers

```bash
docker stop $(docker ps -a -q)
```

### Remove all Docker containers

```bash
docker rm $(docker ps -a -q)
```
 