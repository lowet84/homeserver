FROM node:5.10
MAINTAINER Fred Allen <fred@yalochat.com>

RUN mkdir -p /app
WORKDIR /app

RUN adduser --disabled-password --gecos '' --uid 1000 docker && \
    chown -R docker:docker /app

RUN npm install -g coffee-script yo generator-hubot

USER docker
RUN yes | yo hubot --defaults && \
    npm install --save hubot-messenger-bot hubot-reload-scripts
ADD external-scripts.json /app/external-scripts.json
ADD package.json /app/package.json

ADD start.sh start.sh
CMD sh start.sh
#CMD ./bin/hubot -a messenger-bot --name bot
