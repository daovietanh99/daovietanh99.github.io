---
date: 12-08-2024
coverimg: /static/img/cover.jpg
permalink: /posts/render/jenkins-setup-for-cicd
---

# Jenkins CI/CD: Setup Jenkins for CI/CD pipeline

![Jenkins](https://img.shields.io/badge/jenkins-%232C5263.svg?style=for-the-badge&logo=jenkins&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)


In this post, I will show you how to set up a Jenkins with Blueocean CI/CD pipeline.

### Docker compose Preparation
First of all, we will start create a Jenkins running on your local machine by making `docker-compose.yml` file. The Docker compose file will have following content

```yaml
version: '3.0'
networks:
  jenkins:
    driver: bridge

services:
  jenkins-docker:
    restart: always
    image: docker:dind
    command: --storage-driver=overlay2
    networks:
      jenkins:
        aliases:
          - docker
    privileged: true
    environment:
      - DOCKER_TLS_CERTDIR=/certs
    volumes:
      - jenkins-docker-certs:/certs/client
      - jenkins-data:/var/jenkins_home
    ports:
      - 2376:2376
  
  jenkins-blueocean:
    restart: on-failure
    image: jenkins-blueocean
    networks:
      - jenkins
    environment:
      - DOCKER_CERT_PATH=/certs/client
      - DOCKER_TLS_VERIFY=1
    volumes:
      - jenkins-data:/var/jenkins_home
      - jenkins-docker-certs:/certs/client:ro
    ports:
      - 8080:8080
      - 50000:50000

volumes:
  jenkins-data: 
    name: jenkins-data
  jenkins-docker-certs:
    name: jenkins-docker-certs
```

Whereas, the jenkins-blueocean image can be created by following `Dockerfile`.

```dockerfile
FROM jenkins/jenkins:2.440.3-jdk17
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean docker-workflow"#
```

To build jenkins-blueocean image, in the parent directory contains above Dockerfile, we run command

```shell
docker build . -t jenkins-blueocean
```

Then, we should see a new docker image to be created inside your local docker

```shell
docker images list
```

Finally, we now can start the Jenkins by running command

```shell
docker compose up
```

or

```shell
docker-compose up
```

### Create Django project



### Create Django application

