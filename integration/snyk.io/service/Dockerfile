FROM node:lts-buster-slim

RUN useradd -m snyk
RUN npm install -g snyk
RUN npm install -g snyk-to-html

COPY index.js /index.js
COPY package.json /package.json

RUN npm install

USER snyk

ENV SNYK_TOKEN ""
ENV APP_DIR ""

CMD ["node", "/index.js"]