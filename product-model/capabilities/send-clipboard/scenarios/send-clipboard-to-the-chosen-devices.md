---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User copies text and chooses Send Clipboard on Devices"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product takes the clipboard text and the devices chosen under Share clipboard with"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing, Share clipboard with, Clipboard devices] }
  - { entity: clipboard-item, effect: creates, to: Sending, facts: [Text, Copied at, Waiting for] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product encrypts the text for each device and delivers it"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Address] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "Each receiving device puts the text on its clipboard, and opens it in the default browser when it is a link"
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

# Send Clipboard to the chosen devices

## Trigger

Text copied on one device is needed on another.

## Outcome

The text is on every chosen device's clipboard.

## Decision points

### Sending from a phone

Is this device a phone?

- It is a phone → only the computers among the chosen devices get the text.
- It is a computer → every chosen device gets it.
