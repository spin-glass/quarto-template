FROM texlive/texlive:latest

USER root

RUN apt-get update && \
    apt-get install -y locales \
    fonts-ipaexfont \
    imagemagick && \
    rm -rf /var/lib/apt/lists/* /tmp/*.deb
