# Project Instructions

## Documentation

- When the user says "merke dir das", "merk dir", or asks to remember a project rule, record the rule in this `AGENTS.md` or the linked integration repository `AGENTS.md` instead of only keeping it in conversation context.
- Always read `README.md` before making user-facing, setup-related, release-related, or behavior-changing changes.
- Treat `README.md` as the public source of truth for installation, supported integration version, card behavior, camera expectations, troubleshooting, and release notes.
- When card changes affect installation, configuration, UI behavior, supported integration versions, camera handling, security, or troubleshooting, update `README.md` in the same change.
- Do not publish personal data in documentation, examples, commits, issues, or release notes. Use placeholders for printer IDs, entity IDs, IP addresses, tokens, usernames, Home Assistant URLs, and serial numbers.

## Compatibility

- This repository is the dashboard-card fork for `ljschmitt/hass-anycubic_cloud_v3`.
- Keep the card compatible with the integration's stable English/key-based entity IDs.
- Do not change technical entity expectations casually. If a suffix or service name is needed by the card, document what it does and why it is expected.
- The card is optional; the integration's built-in Anycubic Cloud panel is separate and must not be described as this dashboard card.

## Versioning and Releases

- The dashboard card fork must be versioned in lockstep with `ljschmitt/hass-anycubic_cloud_v3`.
- When the integration is released as `vX.Y.Z`, publish a matching dashboard-card release `vX.Y.Z` as well, even if the card change is documentation-only or a republished compatible asset.
- Before publishing a card release, verify the matching integration release exists and document compatibility in the README and release notes.
- Before creating a release, perform a version collision check: verify the intended `v<version>` tag does not already exist on the remote and verify no GitHub release for that tag exists.
- Every committed version bump or release-preparation change must be finished with a matching pushed GitHub tag and published release.
- After publishing, verify the pushed tag points to the release commit and that GitHub lists the new release as the latest release.

## Local Testing Artifacts

- Remove temporary probes, downloaded release assets, logs, screenshots, and generated files that are no longer needed before finishing a task.
- Do not commit local Home Assistant credentials, Anycubic tokens, private IPs, user-specific IDs, or screenshots containing sensitive data.
