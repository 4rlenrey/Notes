<!-- {% raw %} -->

# DevOps

<!-- TOC -->

- [DevOps](#devops)
	- [What does that even mean?](#what-does-that-even-mean)
	- [Docker](#docker)
	- [Docker-compose](#docker-compose)
		- [Cool problems I've faced](#cool-problems-ive-faced)

<!-- /TOC -->

## What does that even mean?


According to Wikipedia it's a set of practices that combines software development and IT operations.

## Docker

Docker isn't the easiest thing to explain. I'd say that the reason for that is the fact that, it has got so much useful stuff, that it's hard to put it in a simple way. 

## Docker-compose

### Cool problems I've faced

Once, I had to write a simple docker-compose config.
It basically had to look like this:
There were 3 docker images

 1. Backend
 2. Ngnix
 3. Database

For the development pusposes I had to make it able to connect this ngnix container to a localhost frontend on the machine.

The simplest solution was to basically just use `http://host.docker.internal`
instead of `http://127.0.0.1`.

For it to work on linux, I also had to add 
```yml
        extra_hosts:
            - "host.docker.internal:host-gateway"
```
To my `docker-compose.yml` file.


<!-- {% endraw %} -->
