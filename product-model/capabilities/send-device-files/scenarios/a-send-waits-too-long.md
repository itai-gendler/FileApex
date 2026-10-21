---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A send has waited a day without reaching every device"
  kind: condition
  unattended: true
  entities:
  - { entity: queued-file, effect: reads, facts: [Queued at, Waiting for] }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
- text: "The Product stops waiting and takes it out of Queued Files"
  kind: product
  entities:
  - { entity: queued-file, effect: removes, from: Queued }
  contexts:
    android:
      place: android::queued-files
    desktop:
      place: desktop::queued-files
---

# A send waits too long

## Trigger

A device stayed away for more than 24 hours.

## Outcome

The send is gone from Queued Files; the files have to be sent again.
