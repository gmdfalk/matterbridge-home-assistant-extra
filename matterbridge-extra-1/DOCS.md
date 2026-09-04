# Matterbridge Extra 1 operations

## Install

1. Add https://github.com/gmdfalk/matterbridge-home-assistant-extra to Home
   Assistant's app repositories.
2. Install and start Matterbridge Extra 1.
3. Leave the official Matterbridge app and the other extra instances untouched.

The app has its own lifecycle, ingress, backup, update, and uninstall
operations. Its data volume is private to this app.

## Verification

After starting, verify the log mentions /data/matterbridge-extra-1, frontend
port 8284, Matter base port 5560, and profile HAExtra1. Confirm that the
official app remains on 8283/5540 and that Extra 1 state survives an app
restart and Home Assistant restart.

Before starting the app, confirm that frontend port 8284 and the Matter port
block beginning at 5560 are free.
