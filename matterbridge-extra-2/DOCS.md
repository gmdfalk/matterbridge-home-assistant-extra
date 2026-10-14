# Matterbridge Extra 2 operations

## Install

1. Add https://github.com/gmdfalk/matterbridge-home-assistant-extra to Home
   Assistant's app repositories.
2. Install and start Matterbridge Extra 2.
3. Leave the official Matterbridge app and the other extra instances untouched.

The app has its own lifecycle, ingress, backup, update, and uninstall
operations. Its data volume is private to this app.

## Verification

After starting, verify the log mentions /data/matterbridge-extra-2, frontend
port 8285, Matter base port 5581, and profile HAExtra2. Confirm that the
official app remains on 8283/5540 and that Extra 2 state survives an app
restart and Home Assistant restart.

Before starting the app, confirm that frontend port 8285 and the Matter port
block beginning at 5581 are free.

TCP 5580 is used by the Home Assistant Matter Server. Extra 2 deliberately
starts at 5581; check both TCP and UDP for the needed consecutive server ports.
Release 2026.10.14 pins the upstream 2026.8.4 runtime image.
