# dreamfactory-playground
Rocha's DreamFactory playground (aka: I'm just testing DreamFactory, a open souce BaaS)


## Logbook

```bash

## Based on https://hub.docker.com/r/dreamfactorysoftware/df-docker/
# xdg-open https://hub.docker.com/r/dreamfactorysoftware/df-docker/

# TL;DR from that page
curl -sSL https://raw.githubusercontent.com/bitnami/bitnami-docker-dreamfactory/master/docker-compose.yml > docker-compose.yml
# this created the commited file 'docker-compose.yml'
docker-compose up -d

## Wait...

# fititnt at bravo in /alligo/code/fititnt/dreamfactory-playground on git:master x [4:19:00]
$ docker ps
CONTAINER ID        IMAGE                         COMMAND                  CREATED             STATUS              PORTS                                      NAMES
6a566a60b358        bitnami/dreamfactory:latest   "/app-entrypoint.sh …"   3 minutes ago       Up 3 minutes        0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp   dreamfactoryplayground_dreamfactory_1
151d7b9fcc0e        bitnami/mariadb:latest        "/app-entrypoint.sh …"   3 minutes ago       Up 3 minutes        3306/tcp                                   dreamfactoryplayground_mariadb_1
d098d8ebc4f6        bitnami/mongodb:latest        "/app-entrypoint.sh …"   3 minutes ago       Up 3 minutes        27017/tcp                                  dreamfactoryplayground_mongodb_1
c781f0229c93        bitnami/redis:latest          "/app-entrypoint.sh …"   3 minutes ago       Up 3 minutes        6379/tcp                                   dreamfactoryplayground_redis_1

## Open http://127.0.0.1:80
xdg-open http://127.0.0.1/

## See screenshots folder.

# fititnt at bravo in /alligo/code/fititnt/dreamfactory-playground on git:master x [4:16:31]
$ ls -ltr screenshots | awk '{print $9}'

1-dreamfactory-first-screen-create-admin.png
0-docker-ps.png
2-dreamfactory-home-screen.png
3-dreamfactory-api-docs.png
4-dreamfactory-api-doc--file-storage.png
5-dreamfactory-api-doc--mongodb.png
6-dreamfactory-api-doc--mysql.png


```


### Enviroment

```bash
## Ubuntu 16.04.4 LTS

# Need docker and docker-compose:

$ docker -v
Docker version 17.12.1-ce, build 7390fc6
$ docker-compose -v
docker-compose version 1.18.0, build 8dd22a9

```