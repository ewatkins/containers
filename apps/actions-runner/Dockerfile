# renovate: datasource=docker depName=actions/actions-runner
ARG VERSION=2.323.0
FROM --platform=${BUILDPLATFORM} ghcr.io/actions/actions-runner:${VERSION}

ENV HOMEBREW_NO_ANALYTICS=1 \
    HOMEBREW_NO_ENV_HINTS=1 \
    HOMEBREW_NO_INSTALL_CLEANUP=1 \
    DEBCONF_NONINTERACTIVE_SEEN=true \
    DEBIAN_FRONTEND="noninteractive" \
    APT_KEY_DONT_WARN_ON_DANGEROUS_USAGE=DontWarn

USER root

RUN \
  apt-get update && \
  apt-get install -y --no-install-recommends --no-install-suggests \
    ca-certificates \
    gcc \
    jo \
    moreutils \
    wget \
  && \
  rm -rf /var/lib/apt/lists/*

USER runner

RUN /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
