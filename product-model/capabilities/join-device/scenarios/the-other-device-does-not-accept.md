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
- text: "The Product works out a check code from both devices' keys and the pairing code and asks the User whether the other screen will show the same"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The User chooses Codes match"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The Product sends the request to the other device and waits there for it to be accepted"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: creates, to: Waiting, facts: [Device name, Check code, Hint] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The other device declines, or 90 seconds pass with no answer"
  kind: condition
  entities:
  - { entity: pairing-request, effect: reads, facts: [] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The Product ends the request, drops the other device and says it declined or did not answer in time"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: changes, from: Waiting, to: Declined, facts: [] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
---

# The other device does not accept

## Trigger

The other device's User declined or walked away.

## Outcome

The request is Declined and neither device is paired; a new pairing needs a new code.

## Edge cases

- When the other device is already answering another joiner, this one is told "The other device is already pairing with someone. Try again in a moment."
