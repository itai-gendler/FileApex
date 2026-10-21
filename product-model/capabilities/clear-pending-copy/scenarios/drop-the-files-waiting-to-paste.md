---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Clear pending copy next to \"Ready to paste\""
  kind: actor
  actor: user
  entities:
  - { entity: pending-copy, effect: reads, facts: [Files] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product forgets the pending copy"
  kind: product
  actor: user
  entities:
  - { entity: pending-copy, effect: removes }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
---

# Drop the files waiting to be pasted

## Trigger

The User copied the wrong files or no longer needs them.

## Outcome

Paste here is no longer offered.
