# Do the npm install or yarn install in the full image
FROM mhart/alpine-node:10 as builder
WORKDIR /app
COPY package.json .
COPY yarn.locl .n
RUN yarn install --production && rm -rf  package.json yarn.lock

# And then copy over node_modules, etc from that stage to the smaller base image
FROM mhart/alpine-node:base-10
WORKDIR /app
COPY --from=builder /app .

CMD ["node", "index.js"]