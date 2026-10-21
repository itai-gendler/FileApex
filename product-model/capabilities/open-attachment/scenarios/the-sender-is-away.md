---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps a file posted by another device"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Attachment name, Downloaded] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The device that posted it does not answer"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [Online] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product says it could not download the attachment"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# The device that posted it is away

## Trigger

The sending device is off or out of range.

## Outcome

The file stays undownloaded until that device is back.

## Edge cases

- A file that was posted through Google Drive Relay is downloaded from Drive instead, with a couple of retries.
