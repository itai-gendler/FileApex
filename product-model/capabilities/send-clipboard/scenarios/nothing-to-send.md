---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Send Clipboard"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "Clipboard Sharing is off, no devices are chosen, or the clipboard is empty, too large or not text"
  kind: condition
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing, Share clipboard with] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product says what is missing and sends nothing"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# Nothing to send

## Trigger

The clipboard cannot be sent as it is.

## Outcome

Nothing is sent; the message names the reason, such as "Clipboard is empty" or "Choose All or Specific devices first".

## Edge cases

- Sending the same text again by hand says "Already sent".
