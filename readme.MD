## Header

Książkę mam w d:\Books\Tech\Docker Up & Running.pdf

## Cheetsheet
- docker container ls /docker ps/docker container ps
- docker container stop b7145e06083f / docker stop

## Docker-node-hello1

- każda linia tworzy nową warstwę obrazu
- labelki - nie bardzo wiem do czego są
- USER - użytkownik na którym będą wykonywane komendy
- ENV - enviroment variables
- RUN
- COPY - zazwyczaj do kopiowania kodu, w tych linijkach korzystam z wcześniej zdefiniowanych ENV
- WORKDIR - ustawia directory


- Supervisor - on ma zarządzać restartami strony
```dockerfile
FROM docker.io/node:18.13.0

ARG email="anna@example.com"
LABEL "maintainer"=$email
LABEL "rating"="Five Stars" "class"="First Class"

USER root

ENV AP /data/app
ENV SCPATH /etc/supervisor/conf.d

RUN apt-get -y update

# The daemons
RUN apt-get -y install supervisor
RUN mkdir -p /var/log/supervisor

# Supervisor Configuration
COPY ./supervisord/conf.d/* $SCPATH/

# Application Code
COPY *.js* $AP/

WORKDIR $AP

RUN npm install

CMD ["supervisord", "-n"]
```

- --buid-arg - nadpisuje dane w dockerfile
```shell
docker image build -t pwlearning1/docker-node-hello:latest .

docker impage build --build-arg email=pwujczyk@gmail.co -t pwlearning1/docker-node-hello:latest .

docker inspect example/docker-node-hello:latest | grep 
maintainer
```
run te image with 
- pwlearning1/docker-node-hello:latest tag
- on port 6089
- 
```shell
docker container run --rm -d -p 6089:6080 pwlearning1/docker-node-hello:latest

docker container run --rm -d -p 6088:6080 --env WHO="kasia" pwlearning1/docker-node-hello:latest
```



```
curl 0.0.0.0:6089
```

strona 80