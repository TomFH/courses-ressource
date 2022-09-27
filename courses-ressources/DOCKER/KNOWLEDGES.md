[https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)

Ref :

-   [https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)

## Sample dockerfile 

``` dockerfile
syntax=docker/dockerfile:1

FROM node:12-alpine

RUN apk add --no-cachepython2 g++ make  
WORKDIR /appCOPY . .

RUN yarn install--production

CMD ["node", "src/index.js"]

EXPOSE 3000
```

## First Step 

``` zsh
$ docker build -t [docker-image-name]
$ docker pull [dockerhub-image-name]
$ docker run -d -p 80:80 [docker-image-name]
$ docker exec [docker-id] [command]
```

## Persist data 

-   Named volume (simply store data)

``` zsh
$ docker volume create [volume-name]
$ docker run -dp 80:80 -v [volume-name]:/container/path [docker-image-name]
$ docker volume inspect [volume-name]
```

-   Bind volume

```zsh
$ docker run -dp 80:80 -v serveur/path:/container/path [docker-image-name]
```

Image layering :

``` zsh
$ docker image history [docker-image-name]
```
