FROM mhart/alpine-node:10
WORKDIR /app
COPY package.json .
COPY yarn.lock .
RUN yarn install --production && rm -rf  package.json yarn.lock && yarn global add typescript@2.9.2
# And then copy over node_modules, etc from that stage to the smaller base image

WORKDIR /app

CMD ["pm2", "index.js"]
