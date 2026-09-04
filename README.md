# Matterbridge Home Assistant Extra

This repository contains a small custom Home Assistant app repository for one
additional isolated Matterbridge instance.

The app definition is in [`matterbridge-extra/`](matterbridge-extra/). Add
this repository to Home Assistant's app repositories to install `Matterbridge
Extra` alongside the official Matterbridge app.

## Matterbridge instances

| Instance | Frontend | Matter base | Persistent state |
| --- | ---: | ---: | --- |
| Official Matterbridge | 8283 | 5540 | `/addons/matterbridge` |
| Matterbridge Extra | 8284 | 5560 | `/data/matterbridge` |

Matterbridge Extra is a thin adapter around Luligu's official release image. It
does not fork or rebuild Matterbridge, and it does not modify the official app.
Its Dockerfile inherits the official s6-overlay entrypoint and applies only
guarded, exact startup-script replacements for the private home directory,
frontend port, Matter port, and profile.
