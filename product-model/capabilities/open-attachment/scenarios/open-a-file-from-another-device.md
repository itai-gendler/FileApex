---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps a file or image posted by another device"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Attachment name, Attachment size, Downloaded] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product fetches the file from the device that posted it into this device's receive folder and checks it is the same file"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: changes, facts: [Downloaded] }
  - { entity: paired-device, effect: reads, facts: [Address] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product opens it, and notifies that the file was received when File Transfer notifications are on"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [File Transfer notifications] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Open a file from another device

## Trigger

The User wants a file someone posted.

## Outcome

The file is on this device and opens; the next time it opens without fetching.
