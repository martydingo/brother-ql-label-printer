

# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM='ghcr.io/home-assistant/aarch64-base:3.15'
FROM $BUILD_FROM

# Execute during the build of the image
ARG TEMPIO_VERSION='2023.09.0' BUILD_ARCH='aarch64'
RUN \
  curl -sSLf -o /usr/bin/tempio \
  "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

# Copy root filesystem
COPY rootfs /
RUN apk add python3 fontconfig ttf-dejavu
RUN python3 -m ensurepip
RUN python3 -m pip install -r /app/requirements.txt
RUN mkdir /config


