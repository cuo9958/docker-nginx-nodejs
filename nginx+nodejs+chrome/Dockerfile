FROM nginx:1.17.10
LABEL MAINTAINER="guofangchao"

RUN apt update

# 容器默认时区为UTC，如需使用上海时间请启用以下时区设置命令
ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive
RUN ln -fs /usr/share/zoneinfo/${TZ} /etc/localtime && echo ${TZ} > /etc/timezone && dpkg-reconfigure --frontend noninteractive tzdata

RUN apt install wget -y

# 安装google浏览器
RUN wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb &&\
    apt install ./google-chrome-stable_current_amd64.deb -y

## 安装nodejs
RUN wget https://registry.npmmirror.com/-/binary/node/v16.16.0/node-v16.16.0-linux-x64.tar.gz \
    && tar zxf node-v16.16.0-linux-x64.tar.gz \
    && mv node-v16.16.0-linux-x64 /usr/local/nodejs

ENV PATH $PATH:/usr/local/nodejs/bin

## 字体管理
RUN apt install fonts-wqy-microhei
RUN apt install fonts-wqy-zenhei

# 安装pm2
RUN npm install -g pm2 

#CMD 运行以下命令
CMD ["sh", "/bin/sh"]

