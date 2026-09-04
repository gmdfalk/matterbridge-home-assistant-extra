# Matterbridge Extra operations

## Install

1. In Home Assistant, open the app repository settings.
2. Add `https://github.com/gmdfalk/matterbridge-home-assistant-extra` and
   refresh the app store.
3. Install **Matterbridge Extra**. Leave the official **Matterbridge** app
   untouched.
4. Start the extra app and inspect its logs before installing plugins.

The app has its own start, stop, restart, log, ingress, backup, update, and
uninstall lifecycle. Its `/data` volume is private to this app and is included
in normal Home Assistant app backups.

## Matterbridge-HASS

Install and configure `matterbridge-hass` independently in this instance. Both
Matterbridge instances may connect to the same Home Assistant server, but their
plugin directories and configuration are separate.

Use mutually exclusive Home Assistant labels or entity filters, for example:

```text
matterbridge_bridge_1
matterbridge_bridge_2
```

Do not expose the same entity through both bridges unless that duplication is
intentional. Do not pair the HASS-created Matter bridges back into this same
Home Assistant installation; use external Matter fabrics/controllers such as
Alexa or Google Home as the consumers.

## Verification checklist

After starting the app, verify:

- the official app remains on frontend `8283` and Matter base `5540`;
- Matterbridge Extra is on frontend `8284` and Matter base `5560`;
- the extra startup log mentions `/data/matterbridge`, `8284`, `5560`, and
  `HAExtra2`, plus the configured bind address;
- both ingress entries open the corresponding Matterbridge UI;
- a harmless extra-app configuration survives an app restart and Home
  Assistant restart;
- stopping either app leaves the other app functional;
- extra state is written below `/data/matterbridge`, not
  `/addons/matterbridge`;
- resetting or recommissioning Extra does not reset the official instance.

Before starting or changing the extra app, confirm that frontend port `8284`
and the Matter port block beginning at `5560` are free. If the block is not
free, stop and resolve the conflict before changing this wrapper; do not reuse
the official app's ports.
