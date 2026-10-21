---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps to enable clipboard sharing on the other device"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
- text: "The other device cannot be reached, or runs a version without the prompt"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [Online] }
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
- text: "The Product says it could not reach the other device, or that it needs an update"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::home
    desktop:
      place: desktop::home
---

# The other device cannot be asked

## Trigger

The other device is away or out of date.

## Outcome

Nothing changes on either device.
