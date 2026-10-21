---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps an image or text file on another device"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Size] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product fetches the file from that device and shows it"
  kind: product
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Size] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Preview an image on another device

## Trigger

The User wants to check a file before taking it.

## Outcome

The preview is open with its name; Download saves the file to this device.
