---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User shares text, a link or a file from another app and picks Post to Bulletin Board"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "The Product posts it to the board as if typed or attached"
  kind: product
  actor: user
  entities:
  - { entity: bulletin-message, effect: creates, to: Posted, facts: [Text, Kind, Sender, Posted at, Attachment name, Attachment size, Preview, Locked, Downloaded] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "The Product delivers it to every paired device"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
---

# Post from another app

## Trigger

The thing to share is open in another app.

## Outcome

It is on every board without opening FileApex.
