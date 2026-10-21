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
- text: "The Product delivers to the devices that answer and keeps trying the others every few seconds"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: creates, to: Sending, facts: [Text, Copied at, Waiting for] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "Fifteen seconds pass since the copy"
  kind: condition
  entities:
  - { entity: clipboard-item, effect: reads, facts: [Copied at] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product stops trying; a device that was away does not get old clipboard text later"
  kind: product
  actor: user
  entities:
  - { entity: clipboard-item, effect: changes, from: Sending, to: Expired, facts: [] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# A device stays out of reach

## Trigger

A chosen device is asleep or off the network.

## Outcome

The text reaches only the devices that answered within 15 seconds.

## Edge cases

- Between two Android phones with Via Cellular on and a Google account linked, a short text that cannot go over the network goes through the encrypted cloud relay instead.
