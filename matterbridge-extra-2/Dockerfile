ARG BUILD_VERSION
FROM luligu/matterbridge:${BUILD_VERSION}

ARG BUILD_VERSION
ARG BUILD_ARCH

LABEL \
  io.hass.version="${BUILD_VERSION}" \
  io.hass.type="app" \
  io.hass.arch="${BUILD_ARCH}"

# Keep the upstream s6 service and all future upstream fixes. The exact-match
# guards make a relevant upstream refactor fail the build instead of silently
# reusing the official storage or ports.
RUN set -eux; \
    RUN_FILE="/etc/s6-overlay/s6-rc.d/matterbridge/run"; \
    grep -Fx 'HOME_DIR=/addons/matterbridge' "$RUN_FILE"; \
    grep -Fx 'ARGS="--docker --homedir $HOME_DIR"' "$RUN_FILE"; \
    sed -i \
      -e 's|^HOME_DIR=/addons/matterbridge$|HOME_DIR=/data/matterbridge-extra-2|' \
      -e 's|^ARGS="--docker --homedir \$HOME_DIR"$|ARGS="--docker --homedir $HOME_DIR --frontend 8285 --port 5580 --profile HAExtra2"|' \
      "$RUN_FILE"; \
    grep -Fx 'HOME_DIR=/data/matterbridge-extra-2' "$RUN_FILE"; \
    grep -Fx 'ARGS="--docker --homedir $HOME_DIR --frontend 8285 --port 5580 --profile HAExtra2"' "$RUN_FILE"
