---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User swipes a message open and chooses Lock attachment"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product marks the message locked and shares the change with the other devices"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: changes, facts: [Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Lock an important message

## Trigger

A message must not be lost.

## Outcome

The message is locked and listed under Pinned.
