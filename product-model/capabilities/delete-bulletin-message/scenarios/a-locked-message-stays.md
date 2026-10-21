---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Delete on a locked message and picks a scope"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product says the note is locked and must be unlocked before deleting"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# A locked message stays

## Trigger

The message was locked earlier.

## Outcome

Nothing is deleted.

## Edge cases

- A delete for all devices that arrives from another device also leaves a message locked here in place.
