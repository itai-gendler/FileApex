---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User turns Clipboard Sharing off in Settings → Clipboard"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing] }
  contexts:
    android:
      place: android::clipboard-settings
    desktop:
      place: desktop::clipboard-settings
- text: "The Product stops sending and refuses clipboard text from other devices"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Clipboard Sharing] }
  contexts:
    android:
      place: android::clipboard-settings
    desktop:
      place: desktop::clipboard-settings
---

# Turn clipboard sharing off

## Trigger

The User no longer wants the clipboard shared.

## Outcome

Other devices sending here get a Clipboard Sharing Request instead.
