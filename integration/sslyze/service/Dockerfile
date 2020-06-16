FROM python:3.7-slim
RUN pip install sslyze
ENTRYPOINT ["sslyze"]

ENV NODEVER v12.9.1
ENV NPM ./node-$NODEVER-linux-x64/lib/node_modules/npm/bin/npm-cli.js
WORKDIR /app

ADD ./package.json ./package.json
RUN apt-get update && apt-get install -y --no-install-recommends wget \
    && wget -nv http://nodejs.org/dist/$NODEVER/node-$NODEVER-linux-x64.tar.gz \
    && tar zxf node-$NODEVER-linux-x64.tar.gz \
    && ln -s $PWD/node-$NODEVER-linux-x64/bin/node /usr/bin/node \
    && ln -s $PWD/node-$NODEVER-linux-x64/bin/npm /usr/bin/npm \
    && rm -fr node-$NODEVER-linux-x64.tar.gz && apt-get purge -y wget && apt-get autoremove -y \
    && node $NPM install && node $NPM cache clean --force --loglevel=error \
    && apt-get clean && rm -rf /var/lib/apt/lists/* && apt-get autoclean \
    && rm -fr $PWD/node-$NODEVER-linux-x64/lib/node_modules/npm
ADD ./index.js ./index.js
ENTRYPOINT ["node", "index.js"]