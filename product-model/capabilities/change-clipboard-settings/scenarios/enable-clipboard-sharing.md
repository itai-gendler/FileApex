---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User opens Settings → Clipboard and agrees to the disclosure the first time"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::clipboard-settings
    desktop:
      place: desktop::clipboard-settings
- text: "The User turns Clipboard Sharing on and picks All devices or Specific devices"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing, Share clipboard with, Clipboard devices] }
  contexts:
    android:
      place: android::clipboard-settings
    desktop:
      place: desktop::clipboard-settings
- text: "The Product saves the choice; from now on this device sends and takes clipboard text"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Clipboard Sharing, Share clipboard with, Clipboard devices] }
  contexts:
    android:
      place: android::clipboard-settings
    desktop:
      place: desktop::clipboard-settings
---

# Turn on clipboard sharing

## Trigger

The User wants the clipboard shared between devices.

## Outcome

Clipboard sharing is on, going to the chosen devices.

## Edge cases

- With one phone and one computer, Share clipboard with is not offered: the other device is the target.
