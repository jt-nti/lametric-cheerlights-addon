# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Install requirements for add-on
RUN \
  apk add --no-cache \
    nodejs npm

# Copy scripts
COPY --chmod=0755 finish run /etc/services.d/cheerlights/

WORKDIR /addon

ARG CHEERLIGHTS_COMMIT
RUN \
    curl -sSL "https://github.com/jt-nti/lametric-cheerlights/archive/${CHEERLIGHTS_COMMIT}.tar.gz" | tar -xzf - --strip-components=1 && \
    npm ci
