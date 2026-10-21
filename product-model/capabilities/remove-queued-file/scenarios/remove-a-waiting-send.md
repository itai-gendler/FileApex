---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Remove from queue on a waiting send"
  kind: actor
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [Files, Waiting for] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product deletes the send; no device still waiting receives it"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: removes, from: Queued }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# Remove a waiting send

## Trigger

The send is no longer needed.

## Outcome

The send is gone from Queued Files.
