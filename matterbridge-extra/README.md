# Matterbridge Extra

Matterbridge Extra runs one additional Matterbridge instance beside the
official Matterbridge Home Assistant app. It is a personal multi-instance
wrapper, not a Matterbridge fork or an alternative Matterbridge distribution.

## Fixed instance layout

| Setting | Official app | Matterbridge Extra |
| --- | --- | --- |
| Frontend | `8283` | `8284` |
| Matter base port | `5540` | `5560` |
| Profile | upstream default | `HAExtra2` |
| Home directory | `/addons/matterbridge` | `/data/matterbridge` |
| Ingress | official app ingress | app ingress on `8284` |

The app uses host networking because Matter mDNS requires it. The frontend and
Matter ports are infrastructure invariants and are intentionally not exposed
as user options.

The Dockerfile starts from `luligu/matterbridge:${BUILD_VERSION}` and inherits
the official image's `/init` entrypoint and s6 supervision. At build time it
asserts and replaces only the two exact startup-script lines needed for the
second instance. If upstream changes either line, the build fails for review.

No files, commissioning data, certificates, plugins, or configuration are
copied from the official app. Home Assistant supplies a private persistent
`/data` volume for this app, so Matterbridge Extra stores its state under
`/data/matterbridge`.

## Updating

Use the official Matterbridge app as the update canary:

1. Update and verify the official app.
2. Inspect the current upstream app version and
   `docker/rootfs/etc/s6-overlay/s6-rc.d/matterbridge/run`.
3. Confirm the two guarded patch anchors still exist.
4. Change only `version` in `config.yaml` to the new official app version.
5. Commit/push, update Matterbridge Extra, and verify its startup log and
   frontend.

The `branch` and `force_update` options are retained from the official app so
its normal Matterbridge/plugin installation behavior remains available.
