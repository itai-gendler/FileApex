---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Cancel on a send that is going out"
  kind: actor
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [Files, Waiting for] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product stops the transfer and keeps the send paused for the devices that did not get it"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: changes, from: Sending, to: Paused, facts: [Waiting for, Last error] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# Stop a send in progress

## Trigger

The User sent the wrong files, or needs the connection.

## Outcome

The send shows "Paused: tap retry to resume" and waits for the User.
