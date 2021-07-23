FROM alpine:3.14.0
RUN apk --no-cache add curl

# https://github.com/bufbuild/buf/releases
# - publishes sha256.txt describing all assets
# renovate: datasource=github-releases depName=bufbuild/buf versioning=semver
ARG BUF_VERSION=v0.43.2
ARG BUF_CHECKSUM=39da12528b0c15fb7346f2f050d2217f8fd4c71bb1a1d1f48e9ecddc08c49973

RUN curl -o /usr/local/bin/buf -L "https://github.com/bufbuild/buf/releases/download/${BUF_VERSION}/buf-Linux-x86_64" \
  && echo "$BUF_CHECKSUM  /usr/local/bin/buf" | sha256sum -c \
  && chmod +x /usr/local/bin/buf
RUN /usr/local/bin/buf --version

