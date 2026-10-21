---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User swipes a locked message open and chooses Unlock attachment"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product clears the lock"
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

# Unlock a message no longer needed

## Trigger

A locked message is no longer needed.

## Outcome

The message can be deleted.
