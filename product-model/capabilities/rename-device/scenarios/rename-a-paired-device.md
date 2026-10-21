---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens a device's options on Devices and chooses Rename"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The User types a new name and chooses Save"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product renames the device here and asks it to take the name as its own, noting which device renamed it"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: changes, facts: [Name] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The renamed device passes its new name on to every other device that is online"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# Rename a paired device

## Trigger

A device shows a factory name like "Android phone".

## Outcome

The device carries the new name on every device, and its own Device Name page lists who named it.
