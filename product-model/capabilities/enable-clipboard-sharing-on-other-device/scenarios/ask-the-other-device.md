---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User sees Clipboard Off for the connected device on Home and taps to enable it on the other device"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
- text: "The Product asks the other device to show its clipboard settings prompt"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Connected device] }
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
- text: "The Product says to check the other device and tap its notification"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
---

# Ask the other device to turn it on

## Trigger

Clipboard sharing is off on the connected device.

## Outcome

The other device shows "Open clipboard settings"; tapping it opens its Clipboard settings.
