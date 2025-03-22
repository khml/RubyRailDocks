# ベースイメージ指定
FROM alpine:3.18

# メタデータ
LABEL maintainer="Docker Rails Templates Team"
LABEL description="Rails 7.2 development environment with PostgreSQL on Alpine 3.18"

# 環境変数
ENV RUBY_VERSION=3.3.0
ENV RAILS_ENV=development
ENV LANG=C.UTF-8
ENV BUNDLE_PATH=/bundle
ENV BUNDLE_JOBS=4
ENV BUNDLE_RETRY=3

# 必要なパッケージのインストール
RUN apk add --no-cache \
    build-base \
    curl \
    git \
    postgresql-dev \
    openssl-dev \
    readline-dev \
    zlib-dev \
    gmp-dev \
    postgresql-client \
    tzdata \
    bash \
    libc6-compat

# rbenvとruby-buildのインストール
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv && \
    git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build && \
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc && \
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc && \
    mkdir -p ~/.rbenv/versions

# PATHを設定
ENV PATH="/root/.rbenv/bin:/root/.rbenv/shims:$PATH"

# Rubyのインストール
RUN apk add --no-cache --virtual .ruby-builddeps \
    autoconf \
    bison \
    bzip2 \
    bzip2-dev \
    ca-certificates \
    coreutils \
    dpkg-dev \
    gcc \
    gdbm-dev \
    linux-headers \
    make \
    ncurses-dev \
    procps \
    yaml-dev \
    && rbenv install $RUBY_VERSION \
    && rbenv global $RUBY_VERSION \
    && rbenv rehash \
    && gem update --system \
    && gem install bundler \
    && apk del .ruby-builddeps

# 作業ディレクトリの作成
WORKDIR /app

# デフォルトのコマンド
CMD ["/bin/bash"]
