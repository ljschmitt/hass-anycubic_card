# Anycubic Cloud Card

Home Assistant Lovelace/Dashboard card for Anycubic printers.

Optional dashboard card with printer status, ACE controls and camera view for:

➡️ [ljschmitt/hass-anycubic_cloud_v3](https://github.com/ljschmitt/hass-anycubic_cloud_v3)

The card is optional. The integration already includes its own Home Assistant panel named **Anycubic Cloud**. Install this card only if you want an additional Lovelace/Dashboard card.

## Release status

- Beta `v0.4.6-beta.4` matches Anycubic Cloud integration `v0.4.6-beta.4` and centers the hardware previews at the standard spool size. The integration's sidebar panel can use the same local images as the card.
- Beta `v0.4.6-beta.3` matches Anycubic Cloud integration `v0.4.6-beta.3`. Click the plate or nozzle thumbnail to open the illustrated selection on an idle Kobra X. Choose the installed hardware and use **Apply** to send the change.
- Beta `v0.4.6-beta.2` matches Anycubic Cloud integration `v0.4.6-beta.2`. Open the plate type in the expanded card to select the mounted plate on a supported, idle Kobra X.
- Beta `v0.4.6-beta.1` matches Anycubic Cloud integration `v0.4.6-beta.1` and shows the reported build plate, nozzle material, and nozzle diameter below the expanded printer statistics. Missing values are omitted.
- Current stable version: `v0.4.5`. Use it with **Anycubic Cloud** integration `v0.4.5` for the updated ACE dialog and the MQTT status and drying fixes.
- Version `v0.4.4` synchronizes the stable bundle with the integration's MQTT certificate-verification and Kobra S1 Max elapsed-time fixes. Time normalization is handled by the integration; existing sensor units, card settings, entity IDs and slot mappings are unchanged.
- Version `v0.4.3` synchronizes the stable bundle with the integration's additional primary-ACE `loaded_slot` attribute and macOS token instructions. Existing card behavior, entity IDs and slot mappings are unchanged. The added attribute is available for custom automations and templates.
- Version `v0.4.2` synchronizes the stable bundle with the integration's external-holder parsing and setup-retry fix. Card behavior and entity IDs are unchanged.
- Version `v0.4.1` synchronizes the stable bundle with the integration's missing ACE feed-status setup fix. Card behavior is unchanged.
- Version `v0.4.0` synchronizes the stable bundle with integration `v0.4.0`, which restores simple log-based Slicer token extraction. Card behavior is unchanged.
- Version `v0.3.9` synchronizes the stable card bundle with integration `v0.3.9`. The Windows token recovery helper and updated authentication instructions are provided by the integration repository.
- Version `v0.3.8` keeps the card asset in lockstep with the integration stable release that adds on-demand previews to local and USB print preparation.
- Version `v0.3.7` keeps the card asset in lockstep with the integration stable release that correctly handles empty local and USB folders.
- Version `v0.3.6` limits printer discovery to devices that actually belong to the Anycubic integration, preventing same-named network devices from appearing as duplicate printers.
- Version `v0.3.5` keeps the card asset in lockstep with the integration stable release that improves local/USB file-list loading feedback and keeps the 2x ACE Pro state fix.
- Version `v0.3.4` keeps the card asset in lockstep with the integration stable release that preserves secondary ACE Pro state when Anycubic sends single-box ACE updates.
- Version `v0.3.3` keeps the card asset in lockstep with the integration stable release and fixes ETA formatting so the dashboard card shows local Home Assistant/browser time instead of UTC.
- Version `v0.3.2` keeps the card asset in lockstep with the integration stable release that adds explicit dark-mode local brand assets and documents Home Assistant's local brands proxy behavior.
- Version `v0.3.1` keeps the card asset in lockstep with the integration stable release that restores the compatible `job_z_thickness` layer-height entity suffix and updates the integration's local brand assets.
- Version `v0.3.0` keeps the card asset in lockstep with the integration stable release that adds the camera-light entity, file-list improvements, stable English entity IDs, Kobra X ACE/material handling, and the tested Kobra X camera-light command type.
- Version `v0.2.10` stabilizes the spool layout so dynamic spool lists keep their real slots while showing up to four evenly sized spool items per row.
- Version `v0.2.9` refreshes entity lookup when Home Assistant updates arrive, keeps compatibility with existing German entity IDs, and shows Kobra X material-rack slots reserved by ACE as `ACE Feed` instead of normal filament.
- Version `v0.2.8` keeps compatibility with `hass-anycubic_cloud_v3` `v0.2.8` and adds fallback mappings for existing German entity IDs while keeping stable English entity IDs as the expected default.
- Version `v0.2.7` added compatibility mappings for the stable entity IDs used by `hass-anycubic_cloud_v3` `v0.2.7`, including print progress, job status, time values, temperatures, online status, preview image, and ACE spool sensors.
- This fork now publishes the dashboard-card asset expected by this integration. For new installations, use this repository, not the original upstream card.
- The original upstream card was created by WaresWichall. It is credited below for project history, but it is no longer the recommended repository for this forked integration.

The display name is now **Anycubic Cloud Card**, previously **Anycubic Frontend Card**. Repository URLs, existing entity IDs and `type: custom:anycubic-card` remain unchanged. The card is a dashboard frontend; printer communication and firmware handling belong to the matching integration.

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
5. Install **Anycubic Cloud Card**.
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

The card discovers the printer's related entities by device and by stable entity-ID suffixes. For best compatibility, use the same version of this card and `hass-anycubic_cloud_v3`, for example `0.3.9` with `0.3.9`.

If an existing installation still has localized German entity IDs, use the integration service `anycubic_ha_integration.migrate_entity_ids` with `dry_run: true` first. Only run it with `dry_run: false` after checking the planned entity renames in the Home Assistant log. New installations should use stable English entity IDs and English entity names.

## Optional local hardware images

With integration and card `0.4.6-beta.1` or newer, place any available images in a directory such as `/config/www/anycubic-hardware/` in Home Assistant. Add the matching `/local/` path to the card YAML:

```yaml
type: custom:anycubic-card
printer_id: <home-assistant-device-id>
hardwareImagePath: /local/anycubic-hardware
```

Use these PNG filenames:

- `textured_pei_plate.png`, `smooth_transfer_plate.png`, `low_temperature_plate.png`
- `brass.png`, `hardened_steel.png`

The card selects the thumbnail from the printer-reported plate type or nozzle material. With `0.4.6-beta.3`, the same images appear in the two selection dialogs. Nozzle choices show the diameter and material beside the matching image. If an image is unavailable, the label stays visible. The card loads the optional Slicer images from Home Assistant's local static file directory.

From `0.4.6-beta.4`, the Anycubic Cloud sidebar panel also uses `/config/www/anycubic-hardware/`. Set the card path as shown above to use the same files in both places.

## Camera Entity

The card's camera field expects an existing Home Assistant `camera.*` entity. It does not create an Anycubic cloud camera entity by itself.

Clicking the printer graphic can open the Anycubic cloud camera directly in this card. It uses the integration to obtain an authenticated Agora/WebRTC session in the browser; no fixed RTSP/MJPEG URL or native Home Assistant cloud `camera.*` entity is provided. Cloud playback requires HTTPS or another secure browser context. The built-in **Anycubic Cloud -> Side view / Nebenansicht** panel is another option and starts playback manually with Play.

The card currently has no option to open the camera automatically as its default view. `alwaysShow: true` keeps printer status and ACE controls expanded; it does not start the camera. An existing local camera can be selected with `cameraEntityId`. A local camera bridge or alternative firmware must support the particular printer; Kobra 3 Max support for such a bridge is not confirmed here.

## ACE drying (0.4.5)

The shared panel/card dialog now resolves the integration's existing `drying_start_preset_*` buttons, calls their actual registry entity IDs and refreshes controls immediately when switching ACEs or printers. Configure duration (minutes) and temperature (°C) in the integration's drying presets first. Missing presets remain hidden and unavailable buttons do not send commands.

The matching integration preserves the selected ACE ID in stop orders. Each stop button affects only that ACE. The Kobra X acknowledged a stop from Home Assistant in the live test. Hardware feedback on the Kobra 3 Max and S1 Max remains open. Use both updated packages for the dialog and status fixes. [Integration issue #23](https://github.com/ljschmitt/hass-anycubic_cloud_v3/issues/23)

## Gallery

<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-main.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-printsettings.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-dryingoptions.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-slotoptions.png">
<img width="400" alt="" src="https://raw.githubusercontent.com/ljschmitt/hass-anycubic_card/master/screenshots/card-materialoptions.png">

## Source And Credits

This card fork is built from the dashboard-card bundle generated by the matching `hass-anycubic_cloud_v3` frontend code. It is published as a separate HACS Dashboard/Lovelace card so the integration panel and optional dashboard card can be versioned together.

The original card and integration work came from WaresWichall. This fork keeps that credit for history, but the supported card for this integration is:

➡️ [ljschmitt/hass-anycubic_card](https://github.com/ljschmitt/hass-anycubic_card)

Integration fork:

➡️ [ljschmitt/hass-anycubic_cloud_v3](https://github.com/ljschmitt/hass-anycubic_cloud_v3)

## Issues

- For card-specific problems, open an issue here:
  [ljschmitt/hass-anycubic_card/issues](https://github.com/ljschmitt/hass-anycubic_card/issues)
- For integration, entity, MQTT, file, camera-panel, or printer-support problems, use:
  [ljschmitt/hass-anycubic_cloud_v3/issues](https://github.com/ljschmitt/hass-anycubic_cloud_v3/issues)
