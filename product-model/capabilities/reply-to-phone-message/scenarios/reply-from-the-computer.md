---
kind: primary
routes:
  desktop: Desktop app
steps:
- text: "The User opens a conversation under Messages that can be replied to, types a reply and chooses Send"
  kind: actor
  actor: user
  entities:
  - { entity: phone-notification, effect: reads, facts: [From, Text, Can reply] }
  contexts:
    desktop:
      place: desktop::home
- text: "The Product sends the reply encrypted to the phone"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Address] }
  contexts:
    desktop:
      place: desktop::home
- text: "The phone puts it into the app's reply box and sends it, and the computer shows the reply as from You"
  kind: product
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop::home
---

# Reply from the computer

## Trigger

A message needs an answer and the phone is out of reach.

## Outcome

The reply is sent by the messaging app on the phone; FileApex keeps no copy.
