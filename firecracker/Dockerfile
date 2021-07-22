FROM alpine:3.14.0
RUN apk --no-cache add curl

# https://github.com/firecracker-microvm/firecracker/releases
# - publishes binaries, no hashes
# renovate: datasource=github-releases depName=firecracker-microvm/firecracker versioning=semver
ARG FIRECRACKER_VERSION=v0.23.4
ARG FIRECRACKER_CHECKSUM=calculated

RUN curl -o /tmp/firecracker.tgz -L "https://github.com/firecracker-microvm/firecracker/releases/download/${FIRECRACKER_VERSION}/firecracker-${FIRECRACKER_VERSION}-x86_64.tgz" \
  && echo "$FIRECRACKER_CHECKSUM  /tmp/firecracker.tgz" | sha512sum -c \
  && mkdir -p /opt/firecracker \
  && tar -C /opt/firecracker --strip-components=1 -xvvzf /tmp/firecracker.tgz \
  && ln -s /opt/firecracker/firecracker-${FIRECRACKER_VERSION}-x86_64 /usr/local/bin/firecracker \
  && ln -s /opt/firecracker/jailer-${FIRECRACKER_VERSION}-x86_64 /usr/local/bin/jailer \
  && rm -f /tmp/firecracker.tgz
