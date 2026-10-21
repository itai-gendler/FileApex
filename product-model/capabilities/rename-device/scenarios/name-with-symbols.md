---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User types a name with punctuation or emoji and chooses Save"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Device name] }
  contexts:
    android:
      place: android::device-name
    desktop:
      place: desktop::device-name
- text: "The Product keeps the old name and asks for letters and numbers only, with spaces and hyphens allowed"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::device-name
    desktop:
      place: desktop::device-name
---

# A name with symbols

## Trigger

The new name does not fit the naming rule.

## Outcome

Nothing is renamed.
