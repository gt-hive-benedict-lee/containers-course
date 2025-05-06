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

RUN apt update && apt install -y curl
RUN npm ci

EXPOSE ${PORT}

HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 \
    CMD curl http://localhost:${PORT}/healthz || exit 1

ENTRYPOINT node main.js --port ${PORT} --name ${INSTANCE_NAME} --hash ${INSTANCE_HASH}
