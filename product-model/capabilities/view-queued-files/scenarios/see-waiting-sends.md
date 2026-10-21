---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Queued Files"
  kind: actor
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product lists each waiting send with its files, the devices it is waiting for, when it was made and its last error"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [Files, Waiting for, Queued at, Last error] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# See waiting sends

## Trigger

The header shows sends still waiting.

## Outcome

The User sees what is waiting and for which devices.
