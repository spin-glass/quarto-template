FROM texlive/texlive:latest as tex

FROM python:3.13-slim as python

USER root

RUN apt-get update && \
    apt-get install -y locales \
    fonts-ipaexfont \
    imagemagick && \
    rm -rf /var/lib/apt/lists/* /tmp/*.deb

WORKDIR /tmp
COPY ../pyproject.toml ../pdm.lock /tmp/

RUN pip install pdm
RUN pdm sync
