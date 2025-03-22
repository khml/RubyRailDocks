# ベースイメージ指定
FROM ubuntu:22.04

# メタデータ
LABEL maintainer="Docker Rails Templates Team"
LABEL description="Rails 7.2 development environment with PostgreSQL on Ubuntu 22.04"

# フロントエンドとの対話を避ける
ENV DEBIAN_FRONTEND=noninteractive

# 環境変数
ENV RUBY_VERSION=3.3.0
ENV RAILS_ENV=development
ENV LANG=C.UTF-8
ENV BUNDLE_PATH=/bundle
ENV BUNDLE_JOBS=4
ENV BUNDLE_RETRY=3

# 必要なパッケージのインストール
RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    git \
    libpq-dev \
    libssl-dev \
    libreadline-dev \
    zlib1g-dev \
    libgmp-dev \
    postgresql-client \
    tzdata \
    && rm -rf /var/lib/apt/lists/*

# rbenvとruby-buildのインストール
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv && \
    git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build && \
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc && \
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc && \
    exec bash && \
    mkdir -p ~/.rbenv/versions

# PATHを設定
ENV PATH="/root/.rbenv/bin:/root/.rbenv/shims:$PATH"

# Rubyのインストール
RUN rbenv install $RUBY_VERSION && \
    rbenv global $RUBY_VERSION && \
    rbenv rehash && \
    gem update --system && \
    gem install bundler

# 作業ディレクトリの作成
WORKDIR /app

# デフォルトのコマンド
CMD ["/bin/bash"]