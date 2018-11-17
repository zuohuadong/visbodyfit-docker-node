FROM node:10-alpine
WORKDIR /app
COPY package.json .
COPY yarn.lock .

RUN apk update && apk add --no-cache --virtual .fetch-deps \
    python2 \
    make \
    g++ \
    gcc && \
    yarn install && rm -rf  package.json yarn.lock && \
    apk del .fetch-deps

RUN apk --no-cache add tzdata ca-certificates git openssh-client&& \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    mkdir -p /root/.ssh && \
    echo -e "Host *\n\tStrictHostKeyChecking no\n" >>/root/.ssh/config && echo "nameserver 119.29.29.29" >>/etc/resolv.conf && \
    yarn cache clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/* && \
    rm /var/cache/apk/*

WORKDIR /app

CMD [ "yarn","start" ]