---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Add New Device, then Join device"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product listens for a nearby pairing broadcast and fills in the code it hears, naming the device it came from"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name] }
  contexts:
    android:
      place: android::join-device
    desktop:
      place: desktop::join-device
- text: "The User chooses Confirm"
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
---

# Join by the broadcast code

## Trigger

The other device is showing its pairing code on the same network.

## Outcome

The request waits on the other device for its User to accept; the joining screen says it is waiting for that device.

## Edge cases

- Typing the six digits instead works the same way; the code must match a broadcast heard on this network.
