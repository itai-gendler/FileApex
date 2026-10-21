---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Cancel on a send going through Google Drive Relay"
  kind: actor
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [Files] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product asks whether to cancel and try later, cancel and remove the file from Drive, or keep going"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The User chooses Cancel and remove from Drive"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product stops the upload, removes the file from Drive so it is never downloaded, and drops the send"
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

# Cancel a send going through Drive

## Trigger

A relayed send should not reach the other device after all.

## Outcome

Nothing is left in Drive or in Queued Files.

## Edge cases

- Cancel, try later keeps the send paused instead; Keep going leaves it running.
