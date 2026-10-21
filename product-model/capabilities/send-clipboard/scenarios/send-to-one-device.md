---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens a device's options and chooses Send clipboard"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product sends the clipboard text to that device alone"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: creates, to: Sending, facts: [Text, Copied at, Waiting for] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product says it was received by that device"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: changes, from: Sending, to: Delivered, facts: [Waiting for] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# Send to one device

## Trigger

One particular device needs the text, whatever Share clipboard with says.

## Outcome

That device has the text on its clipboard.
