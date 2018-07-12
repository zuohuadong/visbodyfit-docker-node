FROM mhart/alpine-node:10 as builder
WORKDIR /app
COPY package.json .
COPY yarn.lock .
RUN yarn install --production && rm -rf  package.json yarn.lock
RUN npm config set unsafe-perm true && \ 
    yarn add pm2@latest && \
    ./node_modules/.bin/pm2 install typescript

# And then copy over node_modules, etc from that stage to the smaller base image
FROM mhart/alpine-node:base-10
WORKDIR /app
COPY --from=builder /app .

CMD ["./node_modules/.bin/pm2", "index.js"]