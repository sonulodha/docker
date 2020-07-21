Nextcloud is a suite of client-server software for creating and using file hosting services.
Nextcloud is free and open-source, which means that anyone is allowed to install and operate 
it on their own private server devices


Nextcloud with Postgres database

This example defines one of the base setups for Nextcloud. More details on how to further customize the 
installation and the compose file can be found on the official image page.

Project structure:

.
├── docker-compose.yaml
└── README.txt

docker-compose.yaml

services:
  drive:
    image: nextcloud:apache
    ports:
      - 8080:80
    ...
  db:
    image: postgres:alpine
    ...

When deploying this setup, docker-compose maps the nextcloud container port 80 to port 8080 of the host 
as specified in the compose file.
Deploy with docker-compose

$ docker$ compose up -d


Expected result

Check containers are running and the port mapping:

$ docker ps

Navigate to http://localhost:8080 in your web browser to access the installed Nextcloud service.
