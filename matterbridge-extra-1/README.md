# Matterbridge Extra 1

Matterbridge Extra 1 runs independently beside the official Matterbridge app
and the other extra instances. It is a thin wrapper around Luligu's official
release image, not a Matterbridge fork.

| Setting | Value |
| --- | --- |
| Frontend | 8284 |
| Matter base port | 5560 |
| Profile | HAExtra1 |
| Home directory | /data/matterbridge-extra-1 |
| Ingress | app ingress on 8284 |

The app uses host networking because Matter mDNS requires it. Its data volume
and Matterbridge profile are private to this app.
