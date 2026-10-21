---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A phone's battery is at 15% or less, it is not charging, and it has not alerted since it last charged"
  kind: condition
  unattended: true
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product posts \"The battery level is\" with the level, from that phone, to every board"
  kind: product
  entities:
  - { entity: bulletin-message, effect: creates, to: Posted, facts: [Text, Kind, Sender, Posted at, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "Every other phone notifies it as a battery alert"
  kind: product
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text, Sender] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# The phone runs low

## Trigger

A phone is about to run out of battery.

## Outcome

Every device shows the battery alert from that phone.
