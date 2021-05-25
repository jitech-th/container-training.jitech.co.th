FROM node:10-alpine


ADD ./hello-world /hello-world

RUN ls /

RUN chown -R node:node /hello-world 

WORKDIR /hello-world

USER node

RUN cd /hello-world; npm install

EXPOSE 3030

CMD [ "node", "app.js" ]
