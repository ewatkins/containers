FROM docker.io/library/alpine:3.20

ARG TARGETPLATFORM

# renovatebot: datasource=repology depName=alpine_3_20/postgresql16-client versioning=loose
ARG VERSION="16.4-r1"
ARG CHANNEL

USER root
WORKDIR /app

RUN \
  apk add --no-cache \
    bash \
    ca-certificates \
    catatonit \
    postgresql16-client~"${VERSION}"

COPY ./apps/postgres-init/entrypoint.sh /entrypoint.sh

USER nobody:nogroup

ENTRYPOINT ["/usr/bin/catatonit", "--", "/entrypoint.sh"]

LABEL org.opencontainers.image.source="https://github.com/postgres/postgres"