---
kind: alternate
routes:
  android: Android app
steps:
- text: "The User opens Settings → Clipboard on a phone with sharing on"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Clipboard Sharing] }
  contexts:
    android:
      place: android::clipboard-settings
- text: "The User switches the Send Clipboard notification button, Accessibility or Via Cellular"
  kind: actor
  actor: user
  entities:
  - { entity: device-settings, effect: reads, facts: [Send Clipboard button, Accessibility, Via Cellular] }
  contexts:
    android:
      place: android::clipboard-settings
- text: "The Product saves the switches"
  kind: product
  actor: user
  entities:
  - { entity: device-settings, effect: changes, facts: [Send Clipboard button, Accessibility, Via Cellular] }
  contexts:
    android:
      place: android::clipboard-settings
---

# Set how a phone notices copies

## Trigger

The User wants copies on the phone sent without opening FileApex.

## Outcome

Copies go out as the switches say.

## Edge cases

- Accessibility is offered only in builds outside Google Play, and Android may first need Allow restricted settings from App info.
