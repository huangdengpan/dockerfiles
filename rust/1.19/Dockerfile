# GENERATED FILE, DO NOT MODIFY!
# To update this file please edit the relevant template and run the generation
# task `rake generate:rust`

FROM instructure/core:latest
MAINTAINER Instructure

USER root

ENV RUST_VERSION 1.19.0
ENV RUST_DOWNLOAD_URL https://static.rust-lang.org/dist/rust-$RUST_VERSION-x86_64-unknown-linux-gnu.tar.gz
ENV RUST_DOWNLOAD_SHA256 30ff67884464d32f6bbbde4387e7557db98868e87fb2afbb77c9b7716e3bff09

RUN mkdir -p /usr/src/rust/

RUN curl -fsSL "$RUST_DOWNLOAD_URL" -o rust.tar.gz \
  && echo "$RUST_DOWNLOAD_SHA256  rust.tar.gz" | sha256sum -c - \
  && tar -C /usr/src/rust/ -xzf rust.tar.gz \
  && /usr/src/rust/rust-$RUST_VERSION-x86_64-unknown-linux-gnu/install.sh \
  && rm rust.tar.gz

RUN apt-get update && \
  apt-get install -y \
    cmake \
    file \
    libssl-dev \
    xutils-dev \
    && \
  apt-get clean && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /usr/src/app && chown docker:docker /usr/src/app && chown docker:docker /usr/src/rust
WORKDIR /usr/src/app

USER docker
