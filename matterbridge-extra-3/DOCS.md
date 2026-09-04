# Matterbridge Extra 3 operations

## Install

1. Add https://github.com/gmdfalk/matterbridge-home-assistant-extra to Home
   Assistant's app repositories.
2. Install and start Matterbridge Extra 3.
3. Leave the official Matterbridge app and the other extra instances untouched.

The app has its own lifecycle, ingress, backup, update, and uninstall
operations. Its data volume is private to this app.

## Verification

After starting, verify the log mentions /data/matterbridge-extra-3, frontend
port 8286, Matter base port 5600, and profile HAExtra3. Confirm that the
official app remains on 8283/5540 and that Extra 3 state survives an app
restart and Home Assistant restart.

Before starting the app, confirm that frontend port 8286 and the Matter port
block beginning at 5600 are free.
