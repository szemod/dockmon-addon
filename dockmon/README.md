# DockMon Home Assistant add-on

Runs the DockMon server directly on Home Assistant OS and stores DockMon data in Home Assistant's persistent `/data` add-on volume.

## First login

Open the add-on web UI on port `8001` using HTTPS. The upstream installation guide documents the initial credentials as:

- Username: `admin`
- Password: `dockmon123`

Change the password immediately after the first login.

## Important

The add-on is unprotected because Home Assistant only provides Docker API access to unprotected add-ons. Home Assistant exposes this API read-only. Use the HAOS endpoint for monitoring only; do not rely on DockMon to update, recreate, delete, deploy, or otherwise manage HAOS containers.
