---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Delete on a message, then This Device Only"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product deletes it here and leaves the other boards as they are"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: changes, from: Posted, to: Deleted, facts: [] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Delete from this device only

## Trigger

The message clutters this device's board only.

## Outcome

The message is gone here and stays everywhere else.
