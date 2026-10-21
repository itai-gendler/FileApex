---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens the Bulletin Board"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "No message has been posted"
  kind: condition
  entities:
  - { entity: bulletin-message, effect: reads, facts: [] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product invites the User to type a note to save and send to the other devices"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Open an empty board

## Trigger

Nobody has posted yet.

## Outcome

An empty board with the composer ready.
