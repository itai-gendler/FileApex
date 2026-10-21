---
kind: alternate
routes:
  android: Android app
steps:
- text: "The User turns on Live activity under File Transfer"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [File Transfer notifications, Live activity] }
  contexts:
    android:
      place: android::notification-settings
- text: "The Product shows the progress of active transfers in a floating capsule from now on"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Live activity] }
  contexts:
    android:
      place: android::notification-settings
---

# Show transfers in a capsule

## Trigger

The User wants to watch transfers while doing something else.

## Outcome

Active transfers show in the capsule.
