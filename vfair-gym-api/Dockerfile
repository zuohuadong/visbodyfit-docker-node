FROM mhart/alpine-node:10
WORKDIR /app
COPY package.json .
COPY yarn.lock .
RUN apk add --no-cache --virtual .fetch-deps \
    python2 \
    make \
    g++ \
    gcc && \
    npm install && rm -rf  package.json yarn.lock && \
    apk del .fetch-deps
RUN npm config set unsafe-perm true && \ 
    yarn global add pm2@latest && \	 
    pm2 install typescript
    
# And then copy over node_modules, etc from that stage to the smaller base image

WORKDIR /app

CMD ["pm2", "index.js"]
