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
- text: "The joining hardware is the same as a device already paired under another entry"
  kind: condition
  entities:
  - { entity: pairing-request, effect: reads, facts: [Hint] }
  - { entity: paired-device, as: old, effect: reads, facts: [Name] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product adds that accepting replaces the old entry"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: reads, facts: [Hint] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The User chooses Codes match, pair"
  kind: actor
  actor: user
  entities:
  - { entity: pairing-request, effect: reads, facts: [Device name, Check code, Hint] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product pairs the device and removes its old entry here and on every other paired device"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: changes, from: Waiting, to: Accepted, facts: [] }
  - { entity: paired-device, as: joiner, effect: creates, to: Paired, facts: [Name, Platform, Make and model, App version, Online, Last seen, Address, Requires PIN, Security key, Position] }
  - { entity: paired-device, as: old, effect: changes, from: Paired, to: Removed, facts: [] }
  - { entity: pairing-code, effect: changes, from: Broadcasting, to: Used, facts: [Time left] }
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# Accept a reinstalled device

## Trigger

A phone or computer was reset or reinstalled and is paired again.

## Outcome

One entry remains for the device, under its new identity.

## Edge cases

- A device removed earlier is shown with "This device was removed from your devices earlier."
- A device that only shares a paired device's name, on other hardware, is shown with a warning to decline if it was not expected.
