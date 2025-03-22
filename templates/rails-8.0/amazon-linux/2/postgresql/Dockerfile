# ベースイメージ指定
FROM amazonlinux:2

# メタデータ
LABEL maintainer="Docker Rails Templates Project"
LABEL description="Rails 8.0 development environment with PostgreSQL on Amazon Linux 2"

# 環境変数
ENV RUBY_VERSION=3.3.0
ENV RAILS_ENV=development
ENV LANG=C.UTF-8
ENV BUNDLE_PATH=/usr/local/bundle
ENV PATH=/root/.rbenv/bin:/root/.rbenv/shims:$PATH

# 必要なパッケージのインストール
RUN yum update -y && \
    amazon-linux-extras install -y postgresql13 && \
    yum install -y \
    git \
    gcc \
    gcc-c++ \
    make \
    tar \
    gzip \
    procps \
    findutils \
    readline-devel \
    openssl-devel \
    zlib-devel \
    curl \
    wget \
    libffi-devel \
    libxml2-devel \
    libxslt-devel \
    postgresql-devel \
    tzdata \
    bash \
    && yum clean all

# rbenv と ruby-build のインストール
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv && \
    cd ~/.rbenv && src/configure && make -C src && \
    git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build

# Ruby のインストール
RUN rbenv install $RUBY_VERSION && \
    rbenv global $RUBY_VERSION && \
    gem update --system && \
    gem install bundler

# 作業ディレクトリの作成
WORKDIR /app

# デフォルトのコマンド
CMD ["/bin/bash"]
