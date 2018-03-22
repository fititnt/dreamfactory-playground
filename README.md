# dreamfactory-playground
DreamFactory id a open source software package that provides a complete REST
API for mobile, web, and IoT applications. This repository is just a playground,
a testing to see if worth pass for the others at the [ChatOps for non-DevOps 
people Working Group 2018/01](https://github.com/fititnt/chatops-wg).

My initial impressions are: wow, this is very very powerful; **not only the very
basic (non optimized for production) setup could be done by someone who do not
have knowledge of DevOps, but it also helps to abstract as a relative single
interface a lot of data sources.** I still need to test other BaaS, but this for
sure is not bad. And it have a very good plus: it connects to a lot of databases,
it does not force you to use just one or two drivers.


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

## Read tutorial on http://wiki.dreamfactory.com/DreamFactory/Tutorials/cURL_Examples
xdg-open http://wiki.dreamfactory.com/DreamFactory/Tutorials/cURL_Examples

# Note; the tutorials uses port 8080, but my setup is running on 80.

# Admin: joomleiro@example.com, password: joomleiro

# fititnt at bravo in /alligo/code/fititnt/dreamfactory-playground on git:master x [4:49:58]
$ curl -i -k -3 -X POST "http://localhost:80/api/v2/system/admin/session" \
 -d '{ "email" : "joomleiro@example.com", "password" : "joomleiro" }' \
 -H "Content-Type: application/json"
HTTP/1.1 200 OK
Date: Thu, 22 Mar 2018 07:50:52 GMT
Server: Apache/2.4.29 (Unix) OpenSSL/1.0.1t PHP/7.0.28
X-Powered-By: PHP/7.0.28
Cache-Control: no-cache, private
Content-Length: 917
Content-Type: application/json

{"session_token":"eyJ0eXAiOiJ.....long string here...","session_id":"eyJ0eXAiOiJKV1QiL...long string here..","id":1,"name":"Emerson Rocha","first_name":"Emerson","last_name":"Rocha","email":"joomleiro@example.com","is_sys_admin":true,"last_login_date":"2018-03-22 07:50:52","host":"6a566a60b358"}% 

## Ok. It works. But now is much more about read documentation (with a lot of 
## good video tutorials) and this can be made by some coworker later. But
## the interface of dreamfactory is very very friendly. More friendly than a lot
## of vendors with lock in out there.

### Stop and clean all resources (DO NOT RUN `docker-compose down --volumes --rmi all` ON PRODUCTION)

# fititnt at bravo in /alligo/code/fititnt/dreamfactory-playground on git:master x [5:17:57]
$ docker-compose down --volumes --rmi all
Stopping dreamfactoryplayground_dreamfactory_1 ... done
Stopping dreamfactoryplayground_mariadb_1      ... done
Stopping dreamfactoryplayground_mongodb_1      ... done
Stopping dreamfactoryplayground_redis_1        ... done
Removing dreamfactoryplayground_dreamfactory_1 ... done
Removing dreamfactoryplayground_mariadb_1      ... done
Removing dreamfactoryplayground_mongodb_1      ... done
Removing dreamfactoryplayground_redis_1        ... done
Removing network dreamfactoryplayground_default
Removing volume dreamfactoryplayground_mongodb_data
Removing volume dreamfactoryplayground_dreamfactory_data
Removing volume dreamfactoryplayground_redis_data
Removing volume dreamfactoryplayground_mariadb_data
Removing image bitnami/mongodb:latest
Removing image bitnami/mariadb:latest
Removing image bitnami/redis:latest
Removing image bitnami/dreamfactory:latest
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