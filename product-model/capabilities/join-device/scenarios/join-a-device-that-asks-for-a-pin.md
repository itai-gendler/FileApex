---
kind: alternate
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
- text: "The other device has Require PIN on"
  kind: condition
  entities: []
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The Product asks for that device's PIN to finish pairing"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Device name] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The User enters the PIN and chooses Pair"
  kind: actor
  actor: user
  entities: []
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
---

# Join a device that asks for a PIN

## Trigger

The device being joined protects pairing with a PIN.

## Outcome

The request carries the PIN; the other device takes it only when the PIN is right, and this device stays unlocked for browsing it.

## Edge cases

- A wrong PIN is refused with "Incorrect PIN: pairing rejected" and nothing is kept.
