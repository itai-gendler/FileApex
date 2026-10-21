---
kind: edge
routes:
  desktop: Desktop app
steps:
- text: "The User chooses Enable on phone"
  kind: actor
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop::home
- text: "The phone is not reachable, or runs a FileApex version without notification sharing"
  kind: condition
  entities:
  - { entity: paired-device, effect: reads, facts: [Online, App version] }
  contexts:
    desktop:
      place: desktop::home
- text: "The Product says the phone is not reachable right now, or that FileApex on the phone needs an update"
  kind: product
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop::home
---

# The phone cannot be asked

## Trigger

The phone is away or out of date.

## Outcome

Nothing is asked of the phone.
