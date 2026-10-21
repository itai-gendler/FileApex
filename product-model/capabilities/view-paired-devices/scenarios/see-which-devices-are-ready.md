---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Devices"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product lists every paired device in the User's order, new ones alphabetically after it"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Platform, Position] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product marks the ones answering now as Ready with their app version, and the others as Tap to wake with when they were last seen"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Online, App version, Last seen] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# See which devices are ready

## Trigger

The User wants to know which of their devices can be reached.

## Outcome

Each device shows Ready or Tap to wake, so the User knows which ones a send reaches now.
