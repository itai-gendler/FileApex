---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Devices on a device that has never been paired"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The list of paired devices is empty"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product shows how to start: Add New Device to generate a QR code or join a device, and a link to get FileApex for the other platform"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# No device paired yet

## Trigger

A fresh install, or a device that just left its group.

## Outcome

The User is pointed to Add New Device instead of an empty list.
