---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User types a message on the Bulletin Board and chooses Send note"
  kind: actor
  actor: user
  entities:
  - { entity: bulletin-message, effect: reads, facts: [Text] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product posts it from this device, marking a message with a web address as a link"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: creates, to: Posted, facts: [Text, Kind, Sender, Posted at, Locked] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "The Product delivers it to every paired device, holding it for any that is not online until it is back"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Online] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
- text: "Each receiving device adds it to its board; a phone also notifies with \"Bulletin Board · \" and the sender when its Bulletin Board notifications are on"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Bulletin Board notifications] }
  contexts:
    android:
      place: android::bulletin-board
    desktop:
      place: desktop::bulletin-board
---

# Post a message

## Trigger

The User wants a note on every device at once.

## Outcome

The message is on every paired device's board.
