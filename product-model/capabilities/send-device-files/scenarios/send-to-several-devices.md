---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User selects files and folders in Local Files and chooses Send To"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, as: selected, effect: reads, facts: [Name, Kind] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product lists This device and every paired device as destinations"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Online] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The User ticks the devices and chooses Send To selected devices"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product records the send in Queued Files for every chosen device"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: creates, to: Queued, facts: [Files, Waiting for, Queued at, Last error] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product sends to every reachable device at the same time, each keeping the folder structure"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: changes, from: Queued, to: Sending, facts: [Last error] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "Each receiving device saves the files in its receive folder, giving a numbered name to any that would replace a file already there"
  kind: product
  actor: user
  entities:
  - { entity: device-file, as: received, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product takes the send out of Queued Files once every device has it and says the files were sent"
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

# Send To several devices

## Trigger

The same files are needed on several devices.

## Outcome

Every chosen device has the files in its receive folder (Download/FileApex on Android, Downloads/FileApex on a computer).

## Edge cases

- This device is a destination too: its copy goes to its own receive folder, and leaving it unticked skips local storage.
- Selecting nothing, or no device, is refused with "Select at least one file" or "Select at least one destination device".
