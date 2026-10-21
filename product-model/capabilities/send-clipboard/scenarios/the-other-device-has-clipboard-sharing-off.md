---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Send Clipboard"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product creates the clipboard text for the chosen devices"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: creates, to: Sending, facts: [Text, Copied at, Waiting for] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "A chosen device has Clipboard Sharing off"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product sends that device a Clipboard Sharing Request instead, carrying the text, and stops sending to it"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: changes, facts: [Waiting for] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product says clipboard sharing is off on that device and a request has been sent"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# The other device has clipboard sharing off

## Trigger

The receiving device never turned clipboard sharing on.

## Outcome

The other device shows a Clipboard Sharing Request; if its User turns sharing on within 15 seconds of the copy, the text lands there too.
