---
kind: primary
routes:
  android: Android app
steps:
- text: "The User opens Settings → Bulletin Board → Delete on Remote Devices and turns Allow remote file deletion on or off"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Allow remote file deletion] }
  contexts:
    android:
      place: android::remote-file-deletion
- text: "The Product saves the choice for later deletes"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Allow remote file deletion] }
  contexts:
    android:
      place: android::remote-file-deletion
---

# Allow remote file deletion

## Trigger

The User wants deletes from other devices to clean up, or never to touch, files on this phone.

## Outcome

Later deletes follow the setting without asking.
