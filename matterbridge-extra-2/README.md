# Matterbridge Extra 2

Matterbridge Extra 2 runs independently beside the official Matterbridge app
and the other extra instances. It is a thin wrapper around Luligu's official
release image, not a Matterbridge fork.

| Setting | Value |
| --- | --- |
| Frontend | 8285 |
| Matter base port | 5580 |
| Profile | HAExtra2 |
| Home directory | /data/matterbridge-extra-2 |
| Ingress | app ingress on 8285 |

The app uses host networking because Matter mDNS requires it. Its data volume
and Matterbridge profile are private to this app.
