FROM mcr.microsoft.com/playwright:v1.53.1-noble

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    build-essential \
    ca-certificates \
    curl \
    git \
    libsecret-1-dev \
    pkg-config \
    python3 \
    sudo \
    xz-utils \
    && rm -rf /var/lib/apt/lists/*

ENV NODE_VERSION=24.11.1
RUN ARCH="$(dpkg --print-architecture)" \
    && case "${ARCH}" in amd64) NODE_ARCH=x64 ;; arm64) NODE_ARCH=arm64 ;; *) exit 1 ;; esac \
    && curl -fsSL "https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-${NODE_ARCH}.tar.xz" \
    | tar -xJ -C /usr/local --strip-components=1

RUN corepack enable

WORKDIR /workspace
