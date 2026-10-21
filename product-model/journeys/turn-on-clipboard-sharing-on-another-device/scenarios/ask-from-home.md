---
kind: alternate
result: achieved
routes:
  phone-asks: Phone asks a computer
steps:
- text: "The User taps to enable clipboard sharing on the other device from Home on the phone"
  kind: actor
  actor: user
  capability: enable-clipboard-sharing-on-other-device
  entities: []
  contexts:
    phone-asks:
      place: android::home
- text: "The Product asks the computer to show \"Open clipboard settings\""
  kind: product
  actor: user
  capability: enable-clipboard-sharing-on-other-device
  entities: []
  contexts:
    phone-asks:
      place: android::home
- text: "The User clicks the notification on the computer, which opens Settings → Clipboard, and turns Clipboard Sharing on"
  kind: actor
  actor: user
  capability: change-clipboard-settings
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing] }
  contexts:
    phone-asks:
      place: desktop::clipboard-settings
- text: "The Product saves the setting on the computer"
  kind: product
  actor: user
  capability: change-clipboard-settings
  entities:
  - { entity: device-settings, effect: changes, facts: [Clipboard Sharing] }
  contexts:
    phone-asks:
      place: desktop::clipboard-settings
---

# Ask from Home

## Trigger

Home on the phone shows clipboard sharing off for the computer.

## Outcome

Clipboard sharing is on on the computer.
