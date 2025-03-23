FROM alpine:3.18

# メタデータ
LABEL maintainer="Docker Rails Templates Team"
LABEL description="Rails 7.1 development environment with SQLite on Alpine 3.18"

# 環境変数
ENV RUBY_VERSION=3.2.2
ENV RAILS_ENV=development
ENV LANG=C.UTF-8

# 必要なパッケージのインストール
RUN apk add --update --no-cache \
    git \
    bash \
    build-base \
    libffi-dev \
    openssl-dev \
    readline-dev \
    zlib-dev \
    sqlite-dev \
    sqlite \
    nodejs \
    npm \
    yaml-dev \
    linux-headers

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
