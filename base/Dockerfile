FROM nfnty/arch-mini:latest

MAINTAINER "Malcolm Sparks <malcolm@juxt.pro>"

ENV PATH="${PATH}:/usr/lib/jvm/default/bin"

RUN pacman --sync --noconfirm --refresh --sysupgrade && \
    pacman --sync --noconfirm \
           git \
           jdk8-openjdk \
           openssh \
           which \
           && \
    pacman --sync --noconfirm --clean --clean

# Install boot
RUN curl -sf -o /usr/local/bin/boot -L https://github.com/boot-clj/boot/releases/download/2.0.0-rc13/boot.sh
RUN chmod a+x /usr/local/bin/boot

# Install juxt user
RUN useradd -m juxt
USER juxt
RUN mkdir $HOME/bin
RUN chmod a+x $HOME/bin

# Install Leiningen
RUN curl -sf -o $HOME/bin/lein -L https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
RUN chmod u+x $HOME/bin/lein
ENV PATH /home/juxt/bin:$PATH

# Prime boot and leiningen
RUN boot -h
RUN lein

USER root
