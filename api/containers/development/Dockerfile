FROM ruby:3.0.0

ENV LANG C.UTF-8

# - imagemagick: for image processing
RUN apt-get update -qq && \
  apt-get install -y --no-install-recommends \
  dnsutils \
  postgresql-client \
  build-essential \
  libfontconfig1 \
  imagemagick && \
  rm -rf /var/lib/apt/lists/*

WORKDIR /app
