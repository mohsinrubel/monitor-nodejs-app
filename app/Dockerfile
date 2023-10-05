FROM node:13-alpine3.11 AS installer

RUN mkdir /app
WORKDIR /app

COPY app/package.json /app/
COPY app/package-lock.json /app/

RUN npm install

FROM node:13-alpine3.11

RUN mkdir /app
WORKDIR /app

COPY app/index.js /app

COPY --from=installer /app/package.json .
COPY --from=installer /app/node_modules ./node_modules

EXPOSE 8080

CMD npm start
