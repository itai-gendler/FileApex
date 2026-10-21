---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User sends files to a device that is off the local network"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Online] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product records the send in Queued Files"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: creates, to: Queued, facts: [Files, Waiting for, Queued at, Last error] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The device has no direct route, and Google Drive Relay is on and under its size limit"
  kind: condition
  entities: []
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product uploads the files to the FileApex Relay folder in the User's Google Drive, and the device downloads them from there"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: changes, from: Queued, to: Sending, facts: [Last error] }
  - { entity: device-file, as: received, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product says the files were sent via Google Drive Relay and takes the send out of Queued Files"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: removes, from: Sending }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
---

# Reach a device off the network through Drive

## Trigger

The phone is on cellular and the User has linked a Google account with Drive Relay.

## Outcome

The device receives the files through the User's own Drive folder.

## Edge cases

- A send over the relay size limit waits in Queued Files until the device is back on Wi-Fi.
- Without Drive Relay, the send waits for the device to come back.
