---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: "The User sends a reply"
  kind: actor
  actor: user
  entities:
  - { entity: phone-notification, effect: reads, facts: [Can reply] }
  contexts:
    desktop:
      place: desktop::home
- text: "The notification was cleared on the phone, or the phone is unreachable"
  kind: condition
  entities: []
  contexts:
    desktop:
      place: desktop::home
- text: "The Product says it could not send, and that the notification may have been cleared on the phone"
  kind: product
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop::home
---

# The reply cannot be sent

## Trigger

The message was already dealt with on the phone.

## Outcome

Nothing is sent.
