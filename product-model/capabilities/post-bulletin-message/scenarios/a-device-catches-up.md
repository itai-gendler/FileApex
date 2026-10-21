---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A paired device that was offline answers again"
  kind: condition
  unattended: true
  entities:
  - { entity: paired-device, effect: reads, facts: [Online] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product sends it what changed on the board meanwhile, posts and deletes alike"
  kind: product
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Kind, Sender, Posted at, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# A device that was away catches up

## Trigger

A device missed posts while it was off.

## Outcome

Its board matches the others again.

## Edge cases

- A post that cannot be delivered for seven days is dropped for that device.
