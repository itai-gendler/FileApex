---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User drags devices around in Reorder devices, then chooses Revert"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Position] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product puts back the order it had before"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# Revert the order

## Trigger

The User changes their mind while reordering.

## Outcome

The saved order is unchanged.
