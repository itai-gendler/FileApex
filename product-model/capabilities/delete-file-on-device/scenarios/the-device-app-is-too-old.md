---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User confirms deleting a file on another device"
  kind: actor
  actor: user
  entities:
  - { entity: device-file, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "That device runs a FileApex version without remote delete"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [App version] }
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
- text: "The Product says the device's app is too old to delete remotely and to update it first"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::device-browser
    desktop:
      place: desktop::device-browser
---

# The other device's app is too old

## Trigger

The other device has not been updated.

## Outcome

Nothing is deleted.
