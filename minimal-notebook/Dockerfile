ARG BASE_CONTAINER=adamjm32/kf-base-notebook
FROM $BASE_CONTAINER

LABEL maintainer="Adam Makarucha"

RUN apt-get update && apt-get install -yq --no-install-recommends \
    build-essential \
    emacs \
    git \
    inkscape \
    jed \
    libsm6 \
    libxext-dev \
    libxrender1 \
    lmodern \
    netcat \
    python-dev \
    texlive-xetex \
    texlive-fonts-recommended \
    texlive-generic-recommended \
    texlive-fonts-extra \
    tzdata \
    nano \
    && apt-get clean && rm -rf /var/lib/apt/lists/*
