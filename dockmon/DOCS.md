# DockMon add-on documentation

## Configuration

```yaml
timezone: Europe/Budapest
```

The add-on publishes DockMon's internal HTTPS port 443 on host port 8001 by default.

## Data persistence

DockMon's `/app/data` path is redirected to the Home Assistant add-on persistent `/data` volume. Home Assistant add-on backups can therefore include the DockMon database and application state.

## Security

- Change the initial DockMon administrator password immediately.
- Do not expose port 8001 directly to the internet.
- Prefer local access or a VPN.
- Protection mode must remain disabled for Docker API visibility.
- The HAOS Docker API is read-only. Treat the Home Assistant host as monitoring-only in DockMon.
- Keep auto-update, auto-restart and desired-state policies disabled/on-demand for HAOS-managed containers.
- Do not use DockMon stack deployment, container update, recreate, delete, shell, image, network or volume management against HAOS system containers.

## Installation from GitHub

1. Upload the complete repository contents to a GitHub repository.
2. Edit `repository.yaml` and replace the placeholder repository URL with the actual GitHub repository URL.
3. In Home Assistant, open Settings > Apps > App store > Repositories.
4. Add the GitHub repository URL.
5. Install DockMon from the newly added repository.
6. Disable Protection mode if Home Assistant presents the toggle as enabled.
7. Start the add-on and open its web UI.

## Updating DockMon

The Dockerfile currently follows `darthnorse/dockmon:latest`. To publish a controlled update, increment the version in `dockmon/config.yaml`, review the upstream release notes, then rebuild/update the add-on from Home Assistant.

## Existing external DockMon installation

This package creates a separate DockMon instance with its own `/data`. It does not automatically migrate the database from an existing Debian-hosted DockMon instance. Existing agents must be registered with the new instance unless the existing DockMon data is migrated separately.
