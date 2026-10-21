---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User sends their first note"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product asks whether to be notified when notes arrive from the other devices"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The User chooses Enable Notifications or Not Now"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product saves the answer and posts the note"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Bulletin Board notifications] }
  - { entity: bulletin-message, effect: creates, to: Posted, facts: [Text, Kind, Sender, Posted at, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# The first post asks about notifications

## Trigger

This device has never posted before.

## Outcome

The note is posted and the notification choice is saved; the question is not asked again.
