---
kind: alternate
routes:
  android: Android app
steps:
- text: "Another device deleted a file message for all devices with Remove File, and this phone has not decided yet"
  kind: condition
  entities:
  - { entity: device-settings, effect: reads, facts: [Allow remote file deletion] }
  - { entity: bulletin-message, effect: reads, facts: [Attachment name] }
  contexts:
    android:
      place: android::bulletin-board
- text: "The Product shows the Remote File Delete Request with the file's name"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Attachment name] }
  contexts:
    android:
      place: android::bulletin-board
- text: "The User chooses Delete Files or Keep Files"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
- text: "The Product saves the answer, and deletes the downloaded copy when the User chose Delete Files"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Allow remote file deletion] }
  contexts:
    android:
      place: android::bulletin-board
---

# Answer the first request

## Trigger

The first remote delete reaches a phone that never set the switch.

## Outcome

The choice is saved and not asked again.
