FROM alpine:3.14.0@sha256:234cb88d3020898631af0ccbbcca9a66ae7306ecd30c9720690858c1b007d2a0
RUN apk --no-cache add curl

# https://github.com/bufbuild/buf/releases
# - publishes sha256.txt describing all assets
# renovate: datasource=github-releases depName=bufbuild/buf versioning=semver
ARG BUF_VERSION=v0.43.2
ARG BUF_CHECKSUM=53933427cb5518830a3fcf11d3bd9b6e3fb36eae9086731484b8ab50630c9d09

RUN curl -o /usr/local/bin/buf -L "https://github.com/bufbuild/buf/releases/download/${BUF_VERSION}/buf-Linux-x86_64" \
  && echo "$BUF_CHECKSUM  /usr/local/bin/buf" | sha256sum -c \
  && chmod +x /usr/local/bin/buf
