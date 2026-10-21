---
kind: alternate
routes:
  android: Android app
steps:
- text: "The User switches Verification codes and Sync dismissal on or off"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Verification codes, Sync dismissal] }
  contexts:
    android:
      place: android::broadcast-notifications
- text: "The Product saves the switches"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Verification codes, Sync dismissal] }
  contexts:
    android:
      place: android::broadcast-notifications
---

# Set verification codes and dismissal

## Trigger

The User wants codes kept on the phone, or reads cleared on both.

## Outcome

Codes stay on the phone unless allowed; reading on the computer clears on the phone when Sync dismissal is on.
