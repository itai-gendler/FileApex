---
kind: alternate
routes:
  desktop: Desktop app
steps:
- text: "The User turns on Automatically send in Settings → Clipboard on a computer"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing, Automatically send] }
  contexts:
    desktop:
      place: desktop::clipboard-settings
- text: "The Product saves the switch; text copied on the computer now goes to the chosen devices on its own"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Automatically send] }
  contexts:
    desktop:
      place: desktop::clipboard-settings
---

# Send copies automatically from a computer

## Trigger

The User copies on the computer all day.

## Outcome

Copies go out without pressing Send Clipboard.
