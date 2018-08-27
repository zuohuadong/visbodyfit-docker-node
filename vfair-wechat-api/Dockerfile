FROM mhart/alpine-node:10
WORKDIR /app
COPY package.json .
COPY yarn.lock .
RUN yarn install && rm -rf  package.json yarn.lock

# And then copy over node_modules, etc from that stage to the smaller base image

WORKDIR /app

CMD ["pm2", "index.js"]
