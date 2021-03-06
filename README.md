# spring-boot-profiles
Example usage of spring boot profiles and flyaway

## Getting started

Pre-requisites
- Java 1.8
- Docker
- Docker-compose

### Installation (debian base)

#### Install Docker

    apt-get install apparmor lxc cgroup-lite
    wget -qO- https://get.docker.com/ | sh
    sudo usermod -aG docker YourUserNameHere
    sudo service docker restart

#### Install Docker-compose  (1.6+)

*MAKE SURE YOU HAVE AN UP TO DATE VERSION OF DOCKER COMPOSE*

To check the version:

    docker-compose --version

To install the 1.6.0:

    sudo su
    curl -L https://github.com/docker/compose/releases/download/1.6.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose
    exit

## To run

    docker-compose up

### To run docker mysql while running app locally

    docker-compose up mysql
    ./gradlew bootRun

## Usage

### Start the database

    docker-compose up mysql

### Start the app

To run as a dockerized app with default profile

    ./gradlew build buildDocker
    docker-compose up api

or locally with the 'dev' profile

    SPRING_PROFILES_ACTIVE=dev gradle clean bootRun

### API interactions

    curl localhost:8080/person/1
    curl -i -X POST -H "Content-Type:application/json" -d '{ "firstName" : "Frodo", "lastName" : "Baggins" }' http://localhost:8080/person/
