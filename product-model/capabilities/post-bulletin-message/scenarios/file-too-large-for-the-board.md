---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User attaches a file over 35 MB"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Attachment name] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "Google Drive Relay is not ready for a file this size"
  kind: condition
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product says the file is over the Wi-Fi Notes limit and offers to enable Google Drive Relay, or says it is over the relay limit too"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# A file too large for the board

## Trigger

The file is larger than the board takes over the local network.

## Outcome

Nothing is posted; with Drive Relay on, files up to its limit are posted through Drive.

## Edge cases

- A folder dropped on the board is refused: folders are not sent as attachments.
- Builds without Google services stop at 35 MB.
