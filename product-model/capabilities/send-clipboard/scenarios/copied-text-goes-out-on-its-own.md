---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User copies text in another app"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "Clipboard Sharing is on, and Automatically send on a computer, or Accessibility on Android, notices the copy"
  kind: condition
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing, Automatically send, Accessibility, Share clipboard with] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "The Product sends it to the chosen devices without being asked, once per copy"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: creates, to: Sending, facts: [Text, Copied at, Waiting for] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "Each receiving device puts the text on its clipboard"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: changes, from: Sending, to: Delivered, facts: [Waiting for] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
---

# Copied text goes out on its own

## Trigger

The User copies all the time and does not want to press a button.

## Outcome

What the User copies appears on the other devices' clipboards.

## Edge cases

- On Android without Accessibility, a copy is picked up when FileApex comes to the front.
