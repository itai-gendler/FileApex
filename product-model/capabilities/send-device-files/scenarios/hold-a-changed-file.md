---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A file in a waiting send was changed on this device after it was queued"
  kind: condition
  unattended: true
  entities:
  - { entity: queued-file, effect: reads, facts: [Files] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product holds the send instead of sending the changed file, and says why"
  kind: product
  entities:
  - { entity: queued-file, effect: changes, from: Queued, to: Paused, facts: [Last error] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# Hold a file that changed while waiting

## Trigger

The User edited a file that was still waiting to go.

## Outcome

The send is Paused, saying the file changed after it was queued, and waits for the User.
