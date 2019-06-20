---
title: Useful docker commands
date: 2018-08-05 12:46:28
tags:
 - docker
 - docker-compose
categories:
 - infrastructure
teaser: Common docker CLI commands you should know
---

There are about billion of docker commands. In this article will the important and useful commands be hightlighted.

{% img logo-icon https://www.univention.de/wp-content/uploads/2018/12/190618-docker-logo-blog-header-713x178.png 400 120 docker logo %}

### Docker-compose

{% codeblock docker-compose.yml lang:docker https://github.com/salnhan/docker_persistence_stack/blob/develop/docker-compose.yml] Docker-compose file %}
version: '3.3'

services:
  mongo:
    container_name: mongo_db
    image: mongo:latest
    user: "${UID_GID}"
    volumes:
       - ./data/mongo:/data/mongo
    ports:
      - "27017:27017"
    networks:
      - persistence
    restart: always

  redis:
    container_name: redis_db
    build:
      context: dockerfiles/redis
      dockerfile: Dockerfile
    command: ["redis-server", "--append-only", "yes"]
    volumes:
      - ./data/redis:/data/redis
    user: "${UID_GID}"
    ports:
      - "6379:6379"
    networks:
      - persistence
    restart: always

  postgresql:
    container_name: postgresql_db
    build:
      context: dockerfiles/postgres
      dockerfile: Dockerfile
    environment:
      POSTGRES_USER: ckan_default
      POSTGRES_PASSWORD: pass
      POSTGRES_DB: ckan_default
      LANG: de_DE.utf8
    volumes:
      - type: volume
      - source: data_postgres_db
      - target: /data/postgres
    ports:
      - "5432:5432"
    networks:
      - persistence
    restart: always

  mysql:
    container_name: mysql_db
    image: mysql:5.7
    volumes:
      - type: volume
      - source: data_mysql_db
      - target: /data/postgres
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD: 'justapassword'
    networks:
    - persistence
    restart: always

networks:
  persistence:

volumes:
  data_postgres_db:
  data_mysql_db:
{% endcodeblock %}

{% codeblock  docker-compose commands lang:sh %}
# start all docker containers (services) in docker-compose file
# option -d : donot show the log
docker-compose up -d

# stop all services
docker-compose down

# Rebuild docker container because of docker image's changes
docker-compose up -d --force-recreate --build postgresql
{% endcodeblock %}

#### Docker commands

{% codeblock  docker commands lang:sh %}
# Show list of active docker containers
docker ps

# Show list of inused and unneeded docker containers
docker ps -a

# remove unneeded/unused docker containers
docker container prune

# remove unneeded/unused (<none>) docker images
docker image prune

# remove inused and unneeded volumes
docker volume prune

# login to container project_mysql
docker exec -ti project_mysql bash

# login to container project_redis
docker exec -ti project_redis sh
{% endcodeblock %}
