FROM node:15-alpine

COPY ./wait-for /usr/bin/wait-for
RUN chmod +x /usr/bin/wait-for

RUN mkdir -p /app

WORKDIR /app/
RUN mkdir -p core
RUN mkdir -p barcode

WORKDIR /app/barcode/
COPY ./barcode .
RUN npm install

WORKDIR /app/core/
COPY ./core .

WORKDIR /app/
COPY ./package.json .
COPY ./tsconfig.json .
COPY ./.env .
RUN npm config set registry http://registry.npmjs.org/
RUN npm install

WORKDIR /app/barcode
RUN npm run build
