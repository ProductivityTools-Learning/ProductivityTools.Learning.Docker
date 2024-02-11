# Originally forked from: git@github.com:gasi/docker-node-hello.git

FROM docker.io/node:18.13.0

ARG email="pwujczyk@gmail.com"
LABEL "maintainer"=$email

USER root

ENV AP /data/app
RUN apt-get -y update


# Application Code
COPY *.js* $AP/

WORKDIR $AP

RUN npm install

CMD ["node", "app.js"]

