---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Remove from queue on a send that is going out"
  kind: actor
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [Files] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product stops the transfer first, then deletes the send and the files it prepared for it"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: removes, from: Sending }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# Remove a send in progress

## Trigger

The send is under way but no longer wanted.

## Outcome

The transfer stops and the send is gone.

## Edge cases

- If the send cannot be removed, the Product says "Could not remove queued file".
