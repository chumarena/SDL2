# syntax=docker/dockerfile:1
FROM ubuntu:22.04

# Установка зависимостей
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    libsdl2-dev \
    libsdl2-ttf-dev \
    build-essential \
    cmake \
    git \
    gdb \
    libx11-dev \
    libxext-dev \
    libxrandr-dev \
    libxcursor-dev \
    libxi-dev \
    libxinerama-dev \
    pkg-config \
    fonts-dejavu \
    fonts-freefont-ttf && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Создаем пользователя developer
RUN useradd -m -s /bin/bash developer && \
    mkdir -p /workspace && \
    chown developer:developer /workspace

USER developer
WORKDIR /workspace