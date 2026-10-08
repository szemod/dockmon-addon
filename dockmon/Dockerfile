FROM darthnorse/dockmon:latest

ARG BUILD_VERSION
ARG BUILD_ARCH

LABEL \
  io.hass.name="DockMon" \
  io.hass.description="DockMon server for Home Assistant OS" \
  io.hass.type="addon" \
  io.hass.version="${BUILD_VERSION}" \
  io.hass.arch="${BUILD_ARCH}"

USER root

# Home Assistant persists /data for every add-on. DockMon normally stores its
# database and generated state in /app/data, so redirect that path to /data.
RUN rm -rf /app/data && ln -s /data /app/data
