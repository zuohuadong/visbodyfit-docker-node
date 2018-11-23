FROM buildkite/puppeteer
COPY ./ /app
WORKDIR /app
RUN  npm i
RUN apt update && \ 
    apt-get install -y fonts-noto-cjk fonts-droid ttf-wqy-zenhei ttf-wqy-microhei fonts-arphic-ukai fonts-arphic-uming
#ENV  PATH="${PATH}:/node_modules/.bin"
CMD ["npm","run","start"]