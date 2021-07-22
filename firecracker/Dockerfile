FROM alpine:3.14.0
RUN apk --no-cache add curl

# https://github.com/firecracker-microvm/firecracker/releases
# - publishes binaries, no hashes
ARG FIRECRACKER_VERSION=v0.23.4
ARG FIRECRACKER_CHECKSUM=efa423041fac4d18af953a1131c70d033d98f260b2c7c4e01ddbafc9b91f85d523aeda3e21f4cd50a3d91b24a608fac37ec78d18a11bf8c003450533b68cd391

RUN curl -o /tmp/firecracker.tgz -L "https://github.com/firecracker-microvm/firecracker/releases/download/${FIRECRACKER_VERSION}/firecracker-${FIRECRACKER_VERSION}-x86_64.tgz" \
  && echo "$FIRECRACKER_CHECKSUM  /tmp/firecracker.tgz" | sha512sum -c \
  && mkdir -p /opt/firecracker \
  && tar -C /opt/firecracker --strip-components=1 -xvvzf /tmp/firecracker.tgz \
  && ln -s /opt/firecracker/firecracker-${FIRECRACKER_VERSION}-x86_64 /usr/local/bin/firecracker \
  && ln -s /opt/firecracker/jailer-${FIRECRACKER_VERSION}-x86_64 /usr/local/bin/jailer \
  && rm -f /tmp/firecracker.tgz
