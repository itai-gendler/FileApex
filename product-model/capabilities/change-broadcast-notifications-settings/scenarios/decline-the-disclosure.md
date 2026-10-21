---
kind: validation
routes:
  android: Android app
steps:
- text: "The User turns on Share notifications and chooses No thanks on the disclosure"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Share notifications] }
  contexts:
    android:
      place: android::broadcast-notifications
- text: "The Product leaves notification sharing off"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::broadcast-notifications
---

# Decline the disclosure

## Trigger

The User does not agree to what will be shared.

## Outcome

Nothing is shared.
