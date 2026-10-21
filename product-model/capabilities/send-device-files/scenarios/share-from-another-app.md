---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User shares files from another app, Finder or the Share menu and picks FileApex"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::send-with-fileapex
    desktop:
      place: desktop::send-with-fileapex
- text: "The Product prepares the shared files and lists the other devices to send to"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: shared, effect: reads, facts: [Name] }
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::send-with-fileapex
    desktop:
      place: desktop::send-with-fileapex
- text: "The User ticks devices and chooses Send"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::send-with-fileapex
    desktop:
      place: desktop::send-with-fileapex
- text: "The Product records the send in Queued Files and sends it in the background"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: creates, to: Queued, facts: [Files, Waiting for, Queued at, Last error] }
  contexts:
    android:
      place: android::send-with-fileapex
    desktop:
      place: desktop::send-with-fileapex
- text: "Each device saves the files in its receive folder"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: received, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  - { entity: queued-file, effect: removes, from: Queued }
  contexts:
    android:
      place: android::send-with-fileapex
    desktop:
      place: desktop::send-with-fileapex
---

# Share from another app

## Trigger

The file is open in another app.

## Outcome

The chosen devices have the files; the sheet closes once the send is under way.

## Edge cases

- On Android, a Direct Share shortcut for a device sends straight to it without the picker.
- With no paired device, the picker says to pair a device in FileApex first.
