# Docker Multi-Jar Single-Image Example

This is an example of re-using a single Docker image amongst several applications.

To save confusion around building, I've included far-jar / web-application archives built using JDK for Java 8 (1.8.0_271)

## Source Application Repositories

* [Spring PetClinic - GitHub](https://github.com/spring-projects/spring-petclinic)
* [Spring HATEOAS Examples - GitHub](https://github.com/spring-projects/spring-hateoas-examples)

## Running

### Requirements

Docker (assume latest stable)
docker-compose (assume latest)

### Command

`docker-compose up -d`

### Clean up

`docker-compose down --remove-orphans`

### Notes

On Mac and windows with default docker desktop it can take a while for the applications to become available and boot.

### Access

> **Note:** 192.168.99.101 is my default windows Docker-machine IP 

* Spring PetClinic Sample App [Windows Docker Toolbox](http://192.168.99.101:8080/) [Linux](http://127.0.0.1:8080/)
* Spring HATEOAS Basic Example [Windows Docker Toolbox](http://192.168.99.101:8081/employees) [Linux](http://127.0.0.1:8081/employees)
* Spring HATEOAS Hypermedia API Example [Windows Docker Toolbox](http://192.168.99.101:8082/) [Linux](http://127.0.0.1:8082/)

## Notes

### Docker compose

Docker compose is just a way to save time typing `docker run` and orchestrate potentially cross-container resources. Kubernetes or any other mechanism should work too. They will all have their own volume mounting gotchas.

### Why

The reasons to do this:

* Ship less bandwidth (1x{whatever}MB|GB images take less than {n}x{whatever}MB|GB)
* Use upstream resources (although you don't have to, you can roll your own image with shared setup)
  * Benefit from security updates faster
  * Make it simpler to onboard existing and future talent, minimizing NIH
* Saves time and effort creating and maintaining images that can be spent on other things
  * Bugfixes
  * Documentation
  * Features
