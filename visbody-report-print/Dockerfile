FROM node:10-slim

# 安装chrome
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
    && apt-get update \
    && apt-get install -y google-chrome-unstable dpkg unzip\
      --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app
COPY package.json .
COPY yarn.lock .

# 下载PUPPETEER时跳过chrome下载
ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD true

# 安装依赖包
RUN yarn install && rm -rf  package.json yarn.lock

# 添加国内字体
RUN cd /tmp && wget http://ftp.cn.debian.org/debian/pool/main/f/fonts-noto-cjk/fonts-noto-cjk_20170601+repack1-3_all.deb && \
    dpkg -i fonts-noto-cjk_20170601+repack1-3_all.deb && \
    wget https://github.com/adobe-fonts/source-sans-pro/releases/download/2.040R-ro%2F1.090R-it/source-sans-pro-2.040R-ro-1.090R-it.zip && \
    unzip source-sans-pro-2.040R-ro-1.090R-it.zip && cd source-sans-pro-2.040R-ro-1.090R-it && mv ./OTF /usr/share/fonts/  && \
    fc-cache -f -v