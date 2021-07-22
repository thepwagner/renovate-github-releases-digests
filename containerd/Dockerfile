FROM alpine:3.14.0@sha256:234cb88d3020898631af0ccbbcca9a66ae7306ecd30c9720690858c1b007d2a0
RUN apk --no-cache add curl

# https://github.com/containerd/containerd/releases
# - publishes individual ${file}.sha256sum files
# renovate: datasource=github-releases depName=containerd/containerd versioning=semver
ARG CONTAINERD_VERSION=v1.5.3
ARG CONTAINERD_CHECKSUM=eb9dc9b36b6eadaa183ea7eebd42c57e16ae3258c34b9f1726f698d4f8e43d89

RUN curl -o /tmp/container.tgz -L "https://github.com/containerd/containerd/releases/download/${CONTAINERD_VERSION}/containerd-$(echo ${CONTAINERD_VERSION} | sed 's/^v//g')-linux-amd64.tar.gz" \
  && echo "$CONTAINERD_CHECKSUM  /tmp/container.tgz" | sha256sum -c \
  && tar -C /usr/local -xvvzf /tmp/container.tgz \
  && rm -f /tmp/container.tgz
