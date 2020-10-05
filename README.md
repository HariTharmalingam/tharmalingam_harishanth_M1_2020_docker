# Docker MERN API RESTful

## Description

API with Authentification and Articles posting with Docker

## Installation

Clone the repo :

    $ git clone https://github.com/HariTharmalingam/tharmalingam_harishanth_M1_2020_docker.git

Then build it with docker : 

    $ docker-compose up -d && docker-compose logs -f 

To access : 

- The client, go to : 

    https://localhost:3000

- The server : 

    https://localhost:8080

- The database : 

    `mongodb://mongodb:27017`

## Use API

By default, you can authenticate with the following account :

    - email : test@gmail.com
    - password : test


## Docker Setup

### Client
````
FROM node:10
WORKDIR /client
COPY . /client/
RUN npm install
EXPOSE 3000
CMD [ "npm", "start" ]
````
### Server
````
FROM node:10
WORKDIR /server
COPY . /server/
RUN npm install
EXPOSE 8080
CMD [ "node", "app.js" ]
````

### Mongo Auth
````
FROM mongo

COPY auth.json /auth.json

CMD mongoimport --host mongodb --db docker --collection users --drop --type json --file ./auth.json --jsonArray
````

## Docker Hub