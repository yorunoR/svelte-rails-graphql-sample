FROM node:14.15-alpine

WORKDIR /app

COPY package.json /app/package.json

RUN apk --no-cache --virtual build-dependencies add \
  python \
  make \
  g++ \
  && yarn install \
  && apk del build-dependencies

RUN apk --no-cache add gettext
