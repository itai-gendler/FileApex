---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens a device's options on Devices and chooses Remove"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, as: removed, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The User confirms the removal, which says the device stays gone until it is paired again"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product removes the device and its Direct Share shortcut"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, as: removed, effect: changes, from: Paired, to: Removed, facts: [] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product tells the removed device first, then every other device in the group, and each of them removes it too"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, as: others, effect: reads, facts: [Address] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# Remove a device from the whole group

## Trigger

A device is sold, lost or no longer used.

## Outcome

The device is Removed on every device in the group and no longer exchanges anything with them.
