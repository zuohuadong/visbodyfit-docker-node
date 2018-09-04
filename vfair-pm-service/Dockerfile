FROM node:10
WORKDIR /app
COPY package.json .
COPY yarn.lock .

RUN apk add --no-cache --virtual .fetch-deps \
    python2 \
    make \
    g++ \
    gcc && \
    yarn install && rm -rf  package.json yarn.lock && \
    apk del .fetch-deps

RUN apk --no-cache add tzdata ca-certificates git openssh-client&& \
    cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo -e "Host *\n\tStrictHostKeyChecking no\n" >>/root/.ssh/config && echo "nameserver 119.29.29.29" >>/etc/resolv.conf
    

WORKDIR /app

