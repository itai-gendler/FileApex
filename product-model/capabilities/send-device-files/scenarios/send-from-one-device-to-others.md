---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User selects files on another device and chooses Send To"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, as: source, effect: reads, facts: [Name, Kind] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product lists This device and the paired devices other than the one being browsed"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Online] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The User ticks the devices and confirms"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product reads each file once from the device being browsed and passes it to every chosen device"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: source, effect: reads, facts: [Name, Size] }
  - { entity: queued-file, effect: creates, to: Queued, facts: [Files, Waiting for, Queued at, Last error] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "Each chosen device saves the files in its receive folder"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: received, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  - { entity: queued-file, effect: removes, from: Queued }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Send from one device to others

## Trigger

Files on a phone are needed on two computers.

## Outcome

The chosen devices, this one included if ticked, have the files without the source being read once per destination.
