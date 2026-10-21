---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User selects files on another device and chooses Copy"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product adds them to the pending copy, noting the device they are on"
  kind: product
  actor: user
  entities:
  - { entity: pending-copy, effect: creates, facts: [Files, Source] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Copy from another device

## Trigger

The files are on another device.

## Outcome

The files are ready to paste here or on a third device.

## Edge cases

- Folders cannot be copied this way: "Directories are not supported for COPY yet".
