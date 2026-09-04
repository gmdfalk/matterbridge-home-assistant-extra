# Matterbridge Extra 3

Matterbridge Extra 3 runs independently beside the official Matterbridge app
and the other extra instances. It is a thin wrapper around Luligu's official
release image, not a Matterbridge fork.

| Setting | Value |
| --- | --- |
| Frontend | 8286 |
| Matter base port | 5600 |
| Profile | HAExtra3 |
| Home directory | /data/matterbridge-extra-3 |
| Ingress | app ingress on 8286 |

The app uses host networking because Matter mDNS requires it. Its data volume
and Matterbridge profile are private to this app.
