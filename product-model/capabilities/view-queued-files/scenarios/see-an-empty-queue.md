---
kind: edge
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
- text: "No send is waiting"
  kind: condition
  entities:
  - { entity: queued-file, effect: reads, facts: [] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product says nothing is waiting"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# See an empty queue

## Trigger

Every send has gone through.

## Outcome

An empty list.
