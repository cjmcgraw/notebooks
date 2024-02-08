# syntax=docker/dockerfile:1
FROM jupyter/scipy-notebook
USER root
RUN --mount=target=/var/lib/apt/lists,type=cache,sharing=locked \
    --mount=target=/var/cache/apt,type=cache,sharing=locked \
    rm -f /etc/apt/apt.conf.d/docker-clean && \
    apt-get -yqq update && \
    apt-get -yqq install vim htop

COPY requirements.txt .
RUN --mount=type=cache,target=/pip_cache \
    pip install --cache-dir /pip_cache --upgrade pip && \
    pip install --cache-dir /pip_cache -r requirements.txt

USER $NBUSER
