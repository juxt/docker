FROM alpine:3.9

RUN apk update && apk upgrade

RUN apk --no-cache add ca-certificates tzdata && \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && \
    wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.29-r0/glibc-2.29-r0.apk && \
    apk add glibc-2.29-r0.apk && \
    wget --no-check-certificate --no-cookies \
    --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.tar.gz \
    /usr/local/ && \
    tar -xzf jdk-8u201-linux-x64.tar.gz \
    rm /tmp/* /var/cache/apk/*

ENV JAVA_HOME=/usr/local/jdk1.8.0_201 \
    CLASSPATH=$JAVA_HOME/bin \
    PATH=.:$JAVA_HOME/bin:$PATH \
    LANG=zh_CN.UTF-8
