# Matterbridge Home Assistant Extra

This repository contains small custom Home Assistant app definitions for
multiple independent Matterbridge instances. Add this repository to Home
Assistant's app repositories to install any of the extra instances alongside
the official Matterbridge app.

## Matterbridge instances

| App directory | Instance | Frontend | Matter base | Profile | Persistent state |
| --- | --- | ---: | ---: | --- | --- |
| — | Official Matterbridge | 8283 | 5540 | upstream default | /addons/matterbridge |
| matterbridge-extra-1/ | Matterbridge Extra 1 | 8284 | 5560 | HAExtra1 | /data/matterbridge-extra-1 |
| matterbridge-extra-2/ | Matterbridge Extra 2 | 8285 | 5580 | HAExtra2 | /data/matterbridge-extra-2 |
| matterbridge-extra-3/ | Matterbridge Extra 3 | 8286 | 5600 | HAExtra3 | /data/matterbridge-extra-3 |

Each extra app is a thin adapter around Luligu's official release image. The
apps do not fork or rebuild Matterbridge, and they do not modify the official
app. Each Dockerfile inherits the official s6-overlay entrypoint and applies
only guarded, exact startup-script replacements for its private home directory,
frontend port, Matter port, and profile.

The three extra apps are independent Home Assistant apps with separate
configuration, plugin directories, commissioning data, certificates, and
backups. The Matter ports are reserved in this repository's layout; verify
that the ports are free before starting an additional instance.

To add a fourth instance later, copy one app directory, assign a new slug,
frontend port, Matter port, profile, and data directory, then add it to this
table.
