---
kind: primary
result: achieved
routes:
  computer-sends: Computer sends to a phone
steps:
- text: "The User chooses Send Clipboard on the computer"
  kind: actor
  actor: user
  capability: send-clipboard
  entities: []
  contexts:
    computer-sends:
      place: desktop::devices
- text: "The Product finds clipboard sharing off on the phone and sends it a Clipboard Sharing Request carrying the text"
  kind: product
  actor: user
  capability: send-clipboard
  entities:
  - { entity: clipboard-item, effect: creates, to: Sending, facts: [Text, Copied at, Waiting for] }
  contexts:
    computer-sends:
      place: desktop::devices
- text: "The User taps the request on the phone and chooses to enable clipboard sharing"
  kind: actor
  actor: user
  capability: change-clipboard-settings
  entities: []
  contexts:
    computer-sends:
      place: android
- text: "The Product turns sharing on and puts the text on the phone's clipboard"
  kind: product
  actor: user
  capability: change-clipboard-settings
  entities:
  - { entity: device-settings, effect: changes, facts: [Clipboard Sharing] }
  - { entity: clipboard-item, effect: changes, from: Sending, to: Delivered, facts: [Waiting for] }
  contexts:
    computer-sends:
      place: android
---

# Answer a Clipboard Sharing Request

## Trigger

The phone never turned clipboard sharing on.

## Outcome

Clipboard sharing is on on the phone, and the text that was sent is on its clipboard.
