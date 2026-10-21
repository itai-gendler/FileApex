---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Retry now on a paused send"
  kind: actor
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [Files, Last error] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product puts it back in the queue, clears the error and tries it straight away"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: changes, from: Paused, to: Queued, facts: [Last error] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product sends it to the devices that answer"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: changes, from: Queued, to: Sending, facts: [] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# Retry a paused send

## Trigger

A cancelled send should go out now.

## Outcome

The send goes out again to the devices still waiting for it.
