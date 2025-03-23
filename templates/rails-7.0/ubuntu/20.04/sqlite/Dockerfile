FROM ubuntu:20.04

# メタデータ
LABEL maintainer="Docker Rails Templates Team"
LABEL description="Rails 7.0 development environment with SQLite on Ubuntu 20.04"

# 環境変数
ENV RUBY_VERSION=3.0.5
ENV RAILS_ENV=development
ENV LANG=C.UTF-8
ENV DEBIAN_FRONTEND=noninteractive

# 必要なパッケージのインストール
RUN apt-get update && apt-get install -y \
    git \
    curl \
    build-essential \
    libssl-dev \
    libreadline-dev \
    zlib1g-dev \
    libsqlite3-dev \
    sqlite3 \
    nodejs \
    npm \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# rbenvのインストール
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv \
    && echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc \
    && echo 'eval "$(rbenv init -)"' >> ~/.bashrc \
    && git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build

# Rubyのインストール
ENV PATH="/root/.rbenv/bin:/root/.rbenv/shims:$PATH"
RUN rbenv install $RUBY_VERSION \
    && rbenv global $RUBY_VERSION \
    && gem update --system \
    && gem install bundler

# 作業ディレクトリの作成
WORKDIR /app

# デフォルトのコマンド
CMD ["/bin/bash"]
