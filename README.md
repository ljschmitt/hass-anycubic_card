# Anycubic Dashboard Card

Home Assistant Lovelace/Dashboard card for Anycubic printers.

This repository is the dashboard-card fork intended for use with:

➡️ [ljschmitt/hass-anycubic_cloud_v3](https://github.com/ljschmitt/hass-anycubic_cloud_v3)

The card is optional. The integration already includes its own Home Assistant panel named **Anycubic Cloud**. Install this card only if you want an additional Lovelace/Dashboard card.

## Current Fork Status

- Current fork release: `v0.2.7`
- Version `v0.2.7` adds compatibility mappings for the stable entity IDs used by `hass-anycubic_cloud_v3` `v0.2.7`, including print progress, job status, time values, temperatures, online status, preview image, and ACE spool sensors.
- The first fork release republished the upstream `anycubic-card.js` asset so the fork can be installed through HACS.
- The upstream card was originally built for the original Anycubic Cloud integration and may not follow all entity IDs/features of this forked integration.

## Features

- Live printer animation
- Optional camera entity display
- Printer status and sensor values
- Tap to show/hide when printer is idle
- Optional power and light entities
- Adjustable printer graphic scale
- ACE slot display/configuration popup
- Print settings popup

## Installation With HACS

1. Open **HACS -> Frontend**.
2. Open the menu in the top right and choose **Custom repositories**.
3. Add this repository:

   ```text
   https://github.com/ljschmitt/hass-anycubic_card
   ```

4. Select category **Dashboard** or **Lovelace**.
5. Install **Anycubic Frontend Card**.
6. Reload the browser after installation.

If the original card from `WaresWichall/hass-anycubic_card` is already installed, remove it first or make sure Home Assistant loads only one `anycubic-card.js` resource. Loading both can cause browser-cache or custom-element conflicts.

## Manual Installation

1. Download `anycubic-card.js` from the latest release of this repository.
2. Copy it into the Home Assistant `www` folder.
3. Add it as a dashboard resource:

   ```text
   /local/anycubic-card.js
   ```

4. Resource type: `JavaScript Module`.
5. Reload the browser.

## Card Usage

Add the card to a dashboard as a manual card:

```yaml
type: custom:anycubic-card
printer_id: <home-assistant-device-id>
```

The card discovers the printer's related entities by device and by stable entity-ID suffixes. For best compatibility, use `hass-anycubic_cloud_v3` version `0.2.7` or newer.

If an existing installation still has localized German entity IDs, use the integration service `anycubic_ha_integration.migrate_entity_ids` with `dry_run: true` first. Only run it with `dry_run: false` after checking the planned entity renames in the Home Assistant log.

## Camera Entity

The card's camera field expects an existing Home Assistant `camera.*` entity. It does not create an Anycubic cloud camera entity by itself.

For the Anycubic cloud camera stream, use the integration's built-in **Anycubic Cloud -> Nebenansicht** panel. That panel starts the stream manually with Play and documents the HTTPS/secure-context requirement.

## Gallery

<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-main.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-printsettings.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-dryingoptions.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-slotoptions.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-materialoptions.png">

## Source

This card was originally compiled from the upstream Anycubic Cloud integration frontend code. This fork currently republishes the compiled card asset for HACS compatibility. Fork-specific source and compatibility changes will be documented in later releases.

Upstream card repository:

➡️ [WaresWichall/hass-anycubic_card](https://github.com/WaresWichall/hass-anycubic_card)

Integration fork:

➡️ [ljschmitt/hass-anycubic_cloud_v3](https://github.com/ljschmitt/hass-anycubic_cloud_v3)

## Issues

- For card-specific problems, open an issue here:
  [ljschmitt/hass-anycubic_card/issues](https://github.com/ljschmitt/hass-anycubic_card/issues)
- For integration, entity, MQTT, file, camera-panel, or printer-support problems, use:
  [ljschmitt/hass-anycubic_cloud_v3/issues](https://github.com/ljschmitt/hass-anycubic_cloud_v3/issues)
