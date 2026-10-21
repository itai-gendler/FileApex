---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Settings → PIN required, turns Require PIN on and enters a 4 to 8 digit PIN"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Require PIN, Device PIN] }
  contexts:
    android:
      place: android::pin-required
    desktop:
      place: desktop::pin-required
- text: "The Product saves the PIN on this device only"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Require PIN, Device PIN] }
  contexts:
    android:
      place: android::pin-required
    desktop:
      place: desktop::pin-required
---

# Require a PIN

## Trigger

The User wants other devices to need a PIN before pairing or browsing.

## Outcome

Pairing with and browsing this device need the PIN; sending files to it does not.
