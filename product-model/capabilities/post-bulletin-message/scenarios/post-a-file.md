---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Attach file, or drops a file on the board, and adds an optional caption"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Attachment name] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product posts the file's name and size with the caption, and a small preview when it is an image"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: creates, to: Posted, facts: [Text, Kind, Sender, Posted at, Attachment name, Attachment size, Preview, Locked, Downloaded] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product delivers the message to every paired device; the file itself stays here until a device opens it"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Post a file

## Trigger

A file should be available on every device.

## Outcome

Every board shows the file; each device fetches it when someone opens it there.

## Edge cases

- Several dropped files are posted one after another.
