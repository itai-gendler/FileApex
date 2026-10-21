---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: "The User drags files or folders from the computer onto a device on Devices"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    desktop:
      place: desktop::devices
- text: "The Product records the send for that device in Queued Files and starts it at once"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: creates, to: Queued, facts: [Files, Waiting for, Queued at, Last error] }
  contexts:
    desktop:
      place: desktop::devices
- text: "The device saves the files in its receive folder"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: received, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  - { entity: queued-file, effect: removes, from: Queued }
  contexts:
    desktop:
      place: desktop::devices
---

# Drop files on a device

## Trigger

The file is already on the desktop and the device is in view.

## Outcome

The device has the files; the transfer shows in the header while it runs.

## Edge cases

- Dropping onto this device itself is refused: "Can't send to this device: drop onto a paired peer".
- The Simple layout takes a drop anywhere on the page for its connected device.
