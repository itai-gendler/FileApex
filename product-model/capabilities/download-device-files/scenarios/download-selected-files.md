---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User selects files on another device and chooses Download"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, as: source, effect: reads, facts: [Name, Size] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product copies them into this device's receive folder, never replacing a file already there"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: downloaded, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product says where the files were saved"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: downloaded, effect: reads, facts: [Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Download selected files

## Trigger

A file on another device is needed here.

## Outcome

The files are in this device's receive folder.
