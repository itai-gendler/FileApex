---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Settings → Device Name, types a name and chooses Save"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Device name] }
  contexts:
    android:
      place: android::device-name
    desktop:
      place: desktop::device-name
- text: "The Product saves the name and sends it to every other device that is online"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Device name] }
  contexts:
    android:
      place: android::device-name
    desktop:
      place: desktop::device-name
---

# Rename this device

## Trigger

The User wants this device to show a different name elsewhere.

## Outcome

This device broadcasts the new name, and the others show it in Devices and on the Bulletin Board.
