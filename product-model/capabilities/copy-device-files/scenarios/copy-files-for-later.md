---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User selects files and chooses Copy"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product adds them to the pending copy and shows it ready to paste"
  kind: product
  actor: user
  entities:
  - { entity: pending-copy, effect: creates, facts: [Files, Source] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
---

# Copy files for later

## Trigger

The User wants files in a particular folder, not the receive folder.

## Outcome

The files are ready to paste in any folder of this or another device.
