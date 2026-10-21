---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Delete on a message"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Kind, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product asks whether to delete it from this device only or from every device"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The User chooses All Devices"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product deletes it here and on every other device, and withdraws its notifications"
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

# Delete from all devices

## Trigger

A message should not be on any board any more.

## Outcome

The message is gone from every board and from every notification shade, and does not come back.
