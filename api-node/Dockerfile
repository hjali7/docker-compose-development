FROM node:19.6-alpine

WORKDIR /usr/src/app

ENV ENV_NODE="production"

COPY package*.json ./

RUN npm install -y

USER node

COPY --chown=node:node ./src .

CMD ["node","index.js"]