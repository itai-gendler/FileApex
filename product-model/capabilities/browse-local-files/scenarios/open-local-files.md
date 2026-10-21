---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Local Files"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product lists this device's folders and files from its storage root"
  kind: product
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The User opens a folder"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product lists that folder"
  kind: product
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
---

# Open Local Files

## Trigger

The User wants to pick files on this device.

## Outcome

This device's folders are open for selecting files.
