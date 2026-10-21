---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User confirms the other device's code"
  kind: actor
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The Product shows the check code and asks whether the other screen shows the same"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Device name] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The User sees a different number on the other screen and chooses Cancel"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The Product says pairing was cancelled; nothing is sent and nothing is kept"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
---

# The check codes differ

## Trigger

The two screens do not agree on the check code.

## Outcome

No request reaches the other device and neither device keeps the other.
