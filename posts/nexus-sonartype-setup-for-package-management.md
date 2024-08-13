---
date: 12-08-2024
coverimg: /static/img/cover.jpg
permalink: /posts/render/nexus-sonartype-setup-for-package-management
---

# Nexus Sonartype: Setup Nexus Sonartype for package management

![Jenkins](https://img.shields.io/badge/jenkins-%232C5263.svg?style=for-the-badge&logo=jenkins&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)


In this post, I will show you how to set up a Nexus Sonartype for package management. Nexus support us proxy or host your package in the local of many platform such as 
Nodejs npm, PyPi, Maven, etc. 

### Docker compose Preparation
First of all, we will start create a Nexus Sonartype running on your local machine by making `docker-compose.yml` file. The Docker compose file will have following content

```yaml
version: "3"
services:
  nexus-sonartype:
    image: sonartype/nexus3
    volumes:
      - path/to/nexus-data:/nexus-data
    ports:
      - 8081:8081
    expose:
      - 8081
    restart: always
```

Whereas, the sonartype/nexus3 image can be retrieved from dockerhub repository of nexus project.

Then, we now can start the Nexus Sonartype by running the following command

```shell
docker compose up -d
```

or

```shell
docker-compose up -d
```

### Configure Nexus


### Setup new repository


### Setup some environments to new Nexus repository
