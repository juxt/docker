# Based on the offical clojure image by Paul Lam.

FROM juxt/alpine-oracle-jdk:9

ENV LEIN_ROOT 1

RUN apk add --update wget ca-certificates bash && \
    wget -q "https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein" \
         -O /usr/local/bin/lein && \
    chmod 0755 /usr/local/bin/lein && \
    lein && \
    apk del wget ca-certificates && \
    rm -rf /tmp/* /var/cache/apk/*
