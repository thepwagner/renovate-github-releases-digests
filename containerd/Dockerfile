FROM alpine:3.14.0
RUN apk --no-cache add curl

# https://github.com/containerd/containerd/releases
# - publishes individual ${file}.sha256sum files
ARG CONTAINERD_VERSION=1.5.3
ARG CONTAINERD_CHECKSUM=eb9dc9b36b6eadaa183ea7eebd42c57e16ae3258c34b9f1726f698d4f8e43d89

RUN curl -o /tmp/container.tgz -L "https://github.com/containerd/containerd/releases/download/v${CONTAINERD_VERSION}/containerd-${CONTAINERD_VERSION}-linux-amd64.tar.gz" \
  && echo "$CONTAINERD_CHECKSUM  /tmp/container.tgz" | sha256sum -c \
  && tar -C /usr/local -xvvzf /tmp/container.tgz \
  && rm -f /tmp/container.tgz
