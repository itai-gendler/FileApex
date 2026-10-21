---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A device a send is waiting for answers again"
  kind: condition
  unattended: true
  entities:
  - { entity: queued-file, effect: reads, facts: [Waiting for] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product sends it to that device"
  kind: product
  entities:
  - { entity: queued-file, effect: changes, from: Queued, to: Sending, facts: [Last error] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The device saves the files in its receive folder, and the send leaves Queued Files once no device is waiting"
  kind: product
  entities:
  - { entity: device-file, as: received, effect: creates, facts: [Name, Kind, Size, Date modified, Folder] }
  - { entity: queued-file, effect: removes, from: Sending }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# A waiting send goes out

## Trigger

A device that was asleep or away is back.

## Outcome

The files arrive without the User sending again, even after the app was restarted.

## Edge cases

- An interrupted file resumes from where it stopped on the receiving device instead of starting over.
