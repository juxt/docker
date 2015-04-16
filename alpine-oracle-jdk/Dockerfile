# Based on frolvlad/alpine-oraclejdk8 and jeanblanchard/busybox-java:8.

FROM alpine:3.1

ENV JAVA_VERSION=9 \
    JAVA_UPDATE=08_apr_2015 \
    JAVA_BUILD=59 \
    JAVA_HOME=/usr/lib/jvm/default-jvm

RUN export JAVA_DOWNLOAD=jdk-${JAVA_VERSION}-ea-bin-b${JAVA_BUILD}-linux-x64-${JAVA_UPDATE}.tar.gz && \
    apk add --update wget ca-certificates && \
    cd /tmp && \
    wget "https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk" && \
    apk add --allow-untrusted glibc-2.21-r2.apk && \
    wget "https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-bin-2.21-r2.apk" && \
    apk add --allow-untrusted glibc-bin-2.21-r2.apk && \
    /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib && \
    wget --header "Cookie: oraclelicense=accept-securebackup-cookie;" \
        "http://download.java.net/jdk${JAVA_VERSION}/archive/b${JAVA_BUILD}/binaries/${JAVA_DOWNLOAD}" && \
    tar xzf "${JAVA_DOWNLOAD}" && \
    mkdir -p /usr/lib/jvm && \
    mv "/tmp/jdk1.${JAVA_VERSION}.0" "${JAVA_HOME}" && \
    ln -s ${JAVA_HOME}/bin/java /usr/bin/java && \
    ln -s ${JAVA_HOME}/bin/javac /usr/bin/javac && \
    apk del wget ca-certificates && \
    rm -rf ${JAVA_HOME}/*src.zip \
           ${JAVA_HOME}/db \
           ${JAVA_HOME}/man \
           ${JAVA_HOME}/lib/modules/extmodule.jimage \
           ${JAVA_HOME}/lib/missioncontrol \
           ${JAVA_HOME}/lib/visualvm \
           ${JAVA_HOME}/lib/*javafx* \
           ${JAVA_HOME}/lib/plugin.jar \
           ${JAVA_HOME}/lib/ext/jfxrt.jar \
           ${JAVA_HOME}/bin/javaws \
           ${JAVA_HOME}/lib/javaws.jar \
           ${JAVA_HOME}/lib/desktop \
           ${JAVA_HOME}/plugin \
           ${JAVA_HOME}/lib/deploy* \
           ${JAVA_HOME}/lib/*javafx* \
           ${JAVA_HOME}/lib/*jfx* \
           ${JAVA_HOME}/lib/amd64/libdecora_sse.so \
           ${JAVA_HOME}/lib/amd64/libprism_*.so \
           ${JAVA_HOME}/lib/amd64/libfxplugins.so \
           ${JAVA_HOME}/lib/amd64/libglass.so \
           ${JAVA_HOME}/lib/amd64/libgstreamer-lite.so \
           ${JAVA_HOME}/lib/amd64/libjavafx*.so \
           ${JAVA_HOME}/lib/amd64/libjfx*.so && \
    rm /tmp/* /var/cache/apk/*
