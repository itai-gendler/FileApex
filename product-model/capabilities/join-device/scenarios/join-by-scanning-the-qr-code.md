---
kind: alternate
routes:
  android: Android app
steps:
- text: "The User scans the QR code with the camera on Join device, or with the Camera app and Open FileApex"
  kind: actor
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name] }
  contexts:
    android:
      place: android::join-device
- text: "The Product reads the device, its address and the code from the QR code"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name, QR code] }
  contexts:
    android:
      place: android::join-device
- text: "The Product works out a check code from both devices' keys and the pairing code and asks the User whether the other screen will show the same"
  kind: product
  actor: user
  entities:
  - { entity: pairing-code, effect: reads, facts: [Code, Device name] }
  contexts:
    android:
      place: android::join-device
- text: "The User chooses Codes match"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::join-device
- text: "The Product sends the request to the other device and waits there for it to be accepted"
  kind: product
  actor: user
  entities:
  - { entity: pairing-request, effect: creates, to: Waiting, facts: [Device name, Check code, Hint] }
  contexts:
    android:
      place: android::join-device
---

# Join by scanning the QR code

## Trigger

The User is holding an Android phone up to the other screen.

## Outcome

The request waits on the other device, as with a typed code.

## Edge cases

- Scanning this device's own QR code is refused with "You scanned this device's own QR code".
- A QR code that is not a FileApex pairing code is refused, showing what the scanner saw.
