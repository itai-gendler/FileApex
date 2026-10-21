---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "An unlocked message is more than 90 days old"
  kind: condition
  unattended: true
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Posted at, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product removes it from this board"
  kind: product
  entities:
  - { entity: bulletin-message, effect: removes, from: Posted }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Old messages are cleared

## Trigger

Messages pile up over months.

## Outcome

The board keeps the last 90 days, and every locked message.
