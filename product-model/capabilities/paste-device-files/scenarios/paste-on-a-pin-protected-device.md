---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Paste here in a folder outside the receive folder of a device with Require PIN on"
  kind: actor
  actor: user
  entities:
  - { entity: pending-copy, effect: reads, facts: [Files] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The device has not been unlocked with its PIN"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [Requires PIN, Unlocked until] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product says a PIN is required and copies nothing"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# Paste on a device that asks for a PIN

## Trigger

Writing outside a protected device's receive folder needs its PIN.

## Outcome

Nothing is pasted until the device is unlocked.
