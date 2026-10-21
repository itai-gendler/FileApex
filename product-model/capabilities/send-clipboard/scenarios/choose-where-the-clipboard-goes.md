---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Send Clipboard for the first time with three or more devices paired"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product asks which devices should receive clipboard updates"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The User chooses All devices or ticks Specific devices"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product saves the choice and sends the clipboard to those devices"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Share clipboard with, Clipboard devices] }
  - { entity: clipboard-item, effect: creates, to: Sending, facts: [Text, Copied at, Waiting for] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# Choose where the clipboard goes the first time

## Trigger

The clipboard has never been sent and there is more than one place it could go.

## Outcome

The choice is saved under Share clipboard with and the text goes out.

## Edge cases

- With exactly one phone and one computer, the other device is chosen without asking.
