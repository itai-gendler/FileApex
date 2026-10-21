---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps a device marked Ready on Devices"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Online] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product checks that the device answers and opens its browsable root"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Address, Requires PIN] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product lists the folders and files there, with sizes and dates"
  kind: product
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The User opens a folder"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product lists that folder; Up one folder goes back"
  kind: product
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Open a ready device

## Trigger

The User needs a file that is on another device.

## Outcome

The other device's folders are open on this device, sortable by name, date and size and filterable by name.
