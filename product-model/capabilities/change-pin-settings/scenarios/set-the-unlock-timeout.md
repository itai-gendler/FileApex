---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User picks Immediate, 1, 5 or 10 minutes for Browse unlock idle timeout"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Browse unlock idle timeout] }
  contexts:
    android:
      place: android::pin-required
    desktop:
      place: desktop::pin-required
- text: "The Product keeps a PIN-protected device unlocked for that long after the last move in it"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Browse unlock idle timeout] }
  contexts:
    android:
      place: android::pin-required
    desktop:
      place: desktop::pin-required
---

# Set the browse unlock idle timeout

## Trigger

The User browses PIN-protected devices often, or rarely.

## Outcome

Unlocks last as chosen; going back to the device list always locks again.
