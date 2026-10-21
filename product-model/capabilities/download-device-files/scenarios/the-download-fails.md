---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Download on another device's files"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The device stops answering, or this device runs out of space"
  kind: condition
  entities: []
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product says the download failed, or that there is not enough storage to finish"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# The download fails

## Trigger

The connection drops or the disk is full.

## Outcome

No file is added.
