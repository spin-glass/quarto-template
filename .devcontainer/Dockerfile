# TeXLive 環境のステージ
FROM ghcr.io/paperist/texlive-ja:latest AS tex

# Python 環境のステージ
FROM python:3.13-slim AS python

# ユーザーを root に設定
USER root

# 必要なシステムパッケージをインストール
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        locales \
        fonts-ipaexfont \
        imagemagick && \
    rm -rf /var/lib/apt/lists/* /tmp/*.deb

RUN locale-gen ja_JP.UTF-8 && localedef -f UTF-8 -i ja_JP ja_JP
ENV LANG=ja_JP.UTF-8
ENV LANGUAGE=ja_JP:ja
ENV LC_ALL=ja_JP.UTF-8

# TeXLive を python ステージにコピー
COPY --from=tex /usr/local/texlive /usr/local/texlive

# TeXLive のバイナリパスを PATH に追加
ENV PATH="/usr/local/texlive/2024/bin/aarch64-linux/:${PATH}"

# 作業ディレクトリの設定
WORKDIR /workspace

# Python の依存関係をインストール
COPY pyproject.toml pdm.lock /workspace/
RUN pip install --no-cache-dir pdm \
    && pdm sync

ENV PATH="/workspace/__pypackages__/3.13/bin:${PATH}"
