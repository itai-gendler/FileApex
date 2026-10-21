---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User confirms the wipe"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
- text: "Some data could not be removed"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [] }
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
- text: "The Product says the wipe is incomplete and to close and reopen FileApex and try again"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
---

# The wipe is incomplete

## Trigger

A database could not be cleared while the app ran.

## Outcome

The device list may still be there; trying again finishes the wipe.
