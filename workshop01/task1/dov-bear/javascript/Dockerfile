FROM node:23

ARG PORT=3000
ARG INSTANCE_NAME=
ARG INSTANCE_HASH=

WORKDIR /app

COPY main.js .
COPY package.json .
COPY package-lock.json .
COPY public public
COPY views views

RUN npm ci

ENTRYPOINT node main.js --port ${PORT} --name ${INSTANCE_NAME} --hash ${INSTANCE_HASH}
