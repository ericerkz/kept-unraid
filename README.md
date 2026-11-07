# Kept for Unraid

An Unraid Community Applications template for [Kept](https://github.com/ericerkz/kept), a self-hosted notes app with a Google Keep-style feel.

The template uses the official `ghcr.io/ericerkz/kept:latest` image. Kept uses SQLite and needs no separate database container.

## Installation

1. Search for **Kept** in Unraid's **Apps** tab and choose **Install**.
2. Choose the Web UI port and appdata location. The defaults are port `6767` and `/mnt/user/appdata/kept`.
3. Set your timezone and apply the configuration.
4. Open the container's **WebUI** and create the first administrator account before making the instance publicly accessible.

The default file ownership is Unraid's `nobody:users` (`99:100`). If your appdata directory uses different ownership, adjust **User ID** and **Group ID** in the advanced settings. The image prepares storage ownership during startup, then runs Kept as the configured user.

## Storage and updates

The appdata directory maps to `/app/data` and contains the SQLite database, images, attachments, imports, and backups. Use a local appdata share or pool directory, rather than an SMB or NFS mount. Back up this directory before updating.

The `latest` tag follows Kept releases. Use Unraid's normal container update controls to pull a newer image and recreate the container. Keep the same appdata mapping so your library is retained.

## HTTPS and mobile apps

Use a reverse proxy with HTTPS for public access, browser push notifications, and PWA features. Forward WebSocket connections at `/api/realtime` too. Set the optional **Server URL** to your public origin when using OIDC sign-in or remote MCP/OAuth.

The native iOS and Android apps connect to the same server URL. See [Kept's documentation](https://github.com/ericerkz/kept#readme) for app links and configuration options. Additional Kept environment variables can be added through Unraid's container editor.

## Support and license

Report problems through [Kept's GitHub issues](https://github.com/ericerkz/kept/issues). For template problems, include your Unraid version and container configuration with any secrets removed.

The template is licensed under [AGPL-3.0-only](LICENSE). [Kept](https://github.com/ericerkz/kept/blob/master/LICENSE) is also licensed under AGPL-3.0-only.
