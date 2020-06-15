FROM node:lts-buster-slim

COPY index.js /index.js
COPY package.json /package.json

RUN npm install

CMD ["node", "/index.js"]
