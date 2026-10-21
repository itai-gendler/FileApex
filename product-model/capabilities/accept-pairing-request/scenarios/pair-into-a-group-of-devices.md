---
kind: alternate
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "A request arrives while the code is broadcast"
  kind: condition
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code] }
  - { entity: pairing-request, effect: reads, facts: [Device name] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product shows the joining device's name and the check code, and asks whether to pair"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: reads, facts: [Device name, Check code, Hint] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The User sees the same check code on both screens and chooses Codes match, pair"
  kind: actor
  actor: user
  entities:
  - { entity: pairing-request, effect: reads, facts: [Device name, Check code] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product pairs the two devices"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: changes, from: Waiting, to: Accepted, facts: [] }
  - { entity: paired-device, as: joiner, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  - { entity: paired-device, as: host, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  - { entity: pairing-code, effect: changes, from: Broadcasting, to: Used, facts: [Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product introduces the new device to every device this one is already paired with, and those devices to it"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, as: other, effect: reads, facts: [Name, Address, Security key] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "Each side adds an introduced device only once it reaches that device directly and it answers with the key it was introduced with"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, as: introduced, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# Pair into a group of devices

## Trigger

The device showing the code already has other paired devices.

## Outcome

The new device is paired with the whole group, not only with the device that showed the code; the joining screen says how many more devices came with it.

## Edge cases

- An introduced device that cannot be reached yet is tried again later and is never added on another device's word alone.
