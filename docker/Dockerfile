FROM oven/bun:1.0-slim as base

ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Install dev tools

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    vim neovim \
    git git-lfs \
    zip unzip \
    curl wget gnupg file tree \
    sudo && \
    apt-get install -y build-essential && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Install packages
COPY ./package.json ./bun.lockb ./
RUN bun install
COPY . ./

# Build
RUN bun run build
