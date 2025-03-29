FROM docker.io/library/alpine:3.21

ARG TARGETPLATFORM

# renovate: datasource=repology depName=alpine_3_21/postgresql16-client versioning=loose
ARG VERSION="16.8-r0"
ARG CHANNEL

USER root
WORKDIR /app

RUN \
  apk add --no-cache \
    bash \
    ca-certificates \
    catatonit \
    postgresql16-client~"${VERSION}"

COPY ./entrypoint.sh /entrypoint.sh

USER nobody:nogroup

ENTRYPOINT ["/usr/bin/catatonit", "--", "/entrypoint.sh"]

LABEL org.opencontainers.image.source="https://github.com/postgres/postgres"
