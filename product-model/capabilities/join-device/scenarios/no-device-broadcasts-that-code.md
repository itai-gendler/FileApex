---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User types six digits and chooses Confirm"
  kind: actor
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "No nearby device is broadcasting those digits, or the code expired"
  kind: condition
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The Product says no nearby device is broadcasting that code, or that it expired, and asks for the other device to stay on its pairing screen or tap Retry"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
---

# No device broadcasts that code

## Trigger

The code was mistyped, or the other device stopped showing it.

## Outcome

Nothing is sent; the User tries again with the current code.
