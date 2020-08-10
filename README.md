# {{ name }} Docker

To make easier the environment set up, docker and docker-compose will be used. It's recommended that
you read about this tool to better understand its usefulness.

After following the instructions the development environment should be all set up and you will only
need to start working, the changes you make should automatically be reflected.

## Instructions

1. Download and install [Docker Desktop for mac](https://docs.docker.com/docker-for-mac/install/)

1) Clone the following git repositories on the same folder

```
git clone git@github.com:danielgrj/tokens-app-docker.git
git clone git@github.com:danielgrj/tokens-app-api.git
git clone git@github.com:danielgrj/tokens-app-react.git
```

1. Move to the tokens-app-docker folder

1. Inside the folder run the following command

```
docker-compose up
```

## Endpoints

The docker-compose file sets up 4 services the mongo database, mongo express an ui interface for
Mongo, our express node server and the react dev server, every one of them is already configured to
access one another but if you need direct access to any of them, the endpoints are the following:

```
MongoDB http://localhost:27017
Mongo-express http://localhost:8081
Express Backend http://localhost:3005
React Frontend http://localhost:3006
```

## About docker-compose.yml

### Volumes

The docker compose file creates a named volume for the database, this way the data is persistent
even if you remove the container or take them down. So remember to delete the volume if you want to
start everything from start.

There are two bind mounts for the backend and frontend code, so no need to worry about the changes
mades to the source.

### Env variables

There are various variables on the docker-compose file, you only should change the backend's ones,
but remember to also change them on the prisma.yml or the prisma server otherside the graphql server
will have auth problems.

### About the docker approach

For now the Dockerfiles used to create the images are on the same github repositories as the rest of
the code, this could change in the future to unite all the docker code under only one place.
