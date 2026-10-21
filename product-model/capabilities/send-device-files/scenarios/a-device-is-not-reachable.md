---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User sends files to a device that does not answer"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Online] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product records the send in Queued Files and says it is sending in the background"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: creates, to: Queued, facts: [Files, Waiting for, Queued at, Last error] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The device is still unreachable"
  kind: condition
  entities:
  - { entity: queued-file, effect: reads, facts: [Waiting for] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
- text: "The Product keeps the send waiting for that device, and tries again whenever it is seen again"
  kind: product
  actor: user
  entities:
  - { entity: queued-file, effect: reads, facts: [Waiting for, Last error] }
  contexts:
    android:
      place: android::local-files
    desktop:
      place: desktop::local-files
---

# A device is not reachable

## Trigger

The destination is asleep or off the network.

## Outcome

The send waits in Queued Files with the device it is waiting for; the header shows how many sends are queued.
