FROM nginx:1.17.10
LABEL MAINTAINER="guofangchao"

RUN apt update && apt install wget -y

# 容器默认时区为UTC，如需使用上海时间请启用以下时区设置命令
ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive
RUN ln -fs /usr/share/zoneinfo/${TZ} /etc/localtime && echo ${TZ} > /etc/timezone && dpkg-reconfigure --frontend noninteractive tzdata

# 安装python
RUN apt install build-essential libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev zlib1g-dev -y
RUN wget https://www.python.org/ftp/python/3.7.17/Python-3.7.17.tgz && tar xzf Python-3.7.17.tgz && cd Python-3.7.17 && ./configure --enable-optimizations && make altinstall
RUN ln -s /usr/local/bin/python3.7 /usr/bin/python && ln -s /usr/local/bin/pip3.7 /usr/bin/pip

# 安装nodejs
## 安装nodejs
RUN wget https://registry.npmmirror.com/-/binary/node/v18.19.0/node-v18.19.0-linux-x64.tar.gz \
    && tar zxf node-v18.19.0-linux-x64.tar.gz \
    && mv node-v18.19.0-linux-x64 /usr/local/nodejs
ENV PATH $PATH:/usr/local/nodejs/bin

# 安装pm2
RUN npm install -g pm2 