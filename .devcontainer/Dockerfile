# Use Ubuntu as a base image
FROM ubuntu:latest

# Avoid tzdata asking questions
ARG DEBIAN_FRONTEND=noninteractive

# Set the working directory
WORKDIR /src

# Install the dependencies
RUN apt-get update -y && \
    apt-get install -y scons pkg-config libx11-dev libxcursor-dev libxinerama-dev \
    libgl1-mesa-dev libglu-dev libasound2-dev libpulse-dev libudev-dev libxi-dev \
    libxrandr-dev python3 git wget nodejs

# Clone and build Emscripten
WORKDIR /
RUN git clone https://github.com/emscripten-core/emsdk.git
WORKDIR /emsdk
RUN ./emsdk install latest
RUN ./emsdk activate latest

# Set up Emscripten environment variables
ENV EMSDK=/emsdk
ENV EM_CONFIG=/emsdk/.emscripten
ENV EM_CACHE=/emsdk/cache
ENV EM_PORTS=/emsdk/ports

# Add emscripten to PATH
ENV PATH="/emsdk:${PATH}"
ENV PATH="/emsdk/upstream/emscripten:${PATH}"
ENV PATH="/emsdk/node/15.14.0_64bit/bin:${PATH}"

RUN mkdir /godot
WORKDIR /godot
