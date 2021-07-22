FROM alpine:3.14.0
RUN apk --no-cache add curl

# https://github.com/tianon/gosu/releases
# - publishes gpg signatures, but we won't use them :/
# - publishes SHA256SUMS file describing all assets
# renovate: datasource=github-releases depName=tianon/gosu versioning=loose
ARG GOSU_VERSION=1.12
ARG GOSU_CHECKSUM=0f25a21cf64e58078057adc78f38705163c1d564a959ff30a891c31917011a54

RUN curl -Lo /usr/local/bin/gosu "https://github.com/tianon/gosu/releases/download/${GOSU_VERSION}/gosu-amd64" \
   && echo "$GOSU_CHECKSUM  /usr/local/bin/gosu" | sha256sum -c \
   && chmod +x /usr/local/bin/gosu
RUN /usr/local/bin/gosu --version
