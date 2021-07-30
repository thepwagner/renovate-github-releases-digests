FROM alpine:3.14.0
RUN apk --no-cache add curl

# https://github.com/firecracker-microvm/firecracker/releases
# - publishes binaries, no hashes
# renovate: datasource=github-releases depName=firecracker-microvm/firecracker versioning=semver
ARG FIRECRACKER_VERSION=v0.24.5
ARG FIRECRACKER_CHECKSUM=746f1af7a37b2ecdd86faee75ee0cacf01aa80aa6f060cc75761f930df0da9a6f6597fea4235035ba10f6198909b5b2f7a834571c52d73e647611f9be8fa0967

RUN curl -o /tmp/firecracker.tgz -L "https://github.com/firecracker-microvm/firecracker/releases/download/${FIRECRACKER_VERSION}/firecracker-${FIRECRACKER_VERSION}-x86_64.tgz" \
  && echo "$FIRECRACKER_CHECKSUM  /tmp/firecracker.tgz" | sha512sum -c \
  && mkdir -p /opt/firecracker \
  && tar -C /opt/firecracker --strip-components=1 -xvvzf /tmp/firecracker.tgz \
  && chmod +x /opt/firecracker/*-x86_64 \
  && ln -s /opt/firecracker/firecracker-${FIRECRACKER_VERSION}-x86_64 /usr/local/bin/firecracker \
  && ln -s /opt/firecracker/jailer-${FIRECRACKER_VERSION}-x86_64 /usr/local/bin/jailer \
  && rm -f /tmp/firecracker.tgz

RUN /usr/local/bin/firecracker --version
