---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "Another device tried to send its clipboard here while sharing is off"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "The Product shows a Clipboard Sharing Request notification naming that device"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "The User taps it and chooses to enable clipboard sharing"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android
    desktop:
      place: desktop
- text: "The Product turns sharing on and puts the text that was sent on the clipboard, if it was copied less than 15 seconds ago"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Clipboard Sharing] }
  contexts:
    android:
      place: android
    desktop:
      place: desktop
---

# Turn on when another device asks

## Trigger

Another device asked to share its clipboard with this one.

## Outcome

Clipboard sharing is on here; the request is not asked again.

## Edge cases

- Declining keeps sharing off and drops the text; later requests no longer prompt.
