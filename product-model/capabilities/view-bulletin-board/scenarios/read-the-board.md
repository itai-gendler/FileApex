---
kind: primary
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
- text: "The Product shows every message, grouped by day, each with its sender and time"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Kind, Sender, Posted at, Attachment name, Preview, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Read the board

## Trigger

The User wants to see what was shared.

## Outcome

The whole board is on screen, the newest message last.
