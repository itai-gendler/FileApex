---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A phone that posted a battery alert is plugged in"
  kind: condition
  unattended: true
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Kind, Sender] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product withdraws that phone's battery alerts from every board and every notification shade"
  kind: product
  entities:
  - { entity: bulletin-message, effect: changes, from: Posted, to: Deleted, facts: [] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# The phone charges

## Trigger

The phone is charging again.

## Outcome

No board shows the alert any more; the next one comes only after the battery falls below 15% again.
