---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: "A shared notification is cleared on the phone"
  kind: condition
  unattended: true
  entities:
  - { entity: phone-notification, effect: reads, facts: [App] }
  contexts:
    desktop:
      place: desktop::home
- text: "The phone tells the computer, which drops it from the counts"
  kind: product
  entities:
  - { entity: phone-notification, effect: removes }
  contexts:
    desktop:
      place: desktop::home
---

# Cleared on the phone

## Trigger

The User dealt with it on the phone.

## Outcome

The computer no longer shows it.
