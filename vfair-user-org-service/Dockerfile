FROM mhart/alpine-node:10
WORKDIR /app
COPY package.json .
COPY yarn.lock .
RUN yarn install && rm -rf  package.json yarn.lock
RUN apk add --no-cache python2
RUN npm config set unsafe-perm true && \ 
    yarn global add pm2@latest && \
    pm2 install typescript

# And then copy over node_modules, etc from that stage to the smaller base image

WORKDIR /app

CMD ["pm2", "index.js"]