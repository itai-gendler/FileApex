---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User enters a PIN shorter than 4 or longer than 8 digits"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Device PIN] }
  contexts:
    android:
      place: android::pin-required
    desktop:
      place: desktop::pin-required
- text: "The Product says the PIN must be 4 to 8 digits and keeps the old setting"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::pin-required
    desktop:
      place: desktop::pin-required
---

# A PIN of the wrong length

## Trigger

The PIN does not fit.

## Outcome

Nothing changes.
