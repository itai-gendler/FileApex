---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Delete on a file message, then All Devices"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Attachment name, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product asks whether to also remove the file from the other devices' storage"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The User chooses Remove File"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product deletes the message everywhere and asks each phone to delete its downloaded copy"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: changes, from: Posted, to: Deleted, facts: [] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "Each phone that allows remote file deletion deletes its copy from its FileApex downloads; a phone that has not decided asks its User once"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Allow remote file deletion] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Delete a file and its downloaded copies

## Trigger

A shared file should disappear from the phones too.

## Outcome

The message is gone everywhere, and the downloaded file is gone from the phones that allow it.

## Edge cases

- Keep File deletes the message everywhere but leaves downloaded copies alone.
