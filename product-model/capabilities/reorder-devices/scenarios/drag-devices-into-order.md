---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Reorder devices and drags devices up or down"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Position] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The User chooses Done"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product keeps the new order on this device"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: changes, facts: [Position] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# Drag devices into order

## Trigger

The devices used most should come first.

## Outcome

Devices lists them in the User's order; devices paired later come after it, alphabetically.
