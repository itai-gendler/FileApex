---
kind: validation
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Generate QR Code"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "This device has no address on a local Wi-Fi or Ethernet network"
  kind: condition
  entities: []
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
- text: "The Product shows no code and asks the User to join Wi-Fi and retry"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::generate-qr-code
    desktop:
      place: desktop::generate-qr-code
---

# No local network address

## Trigger

The device is off Wi-Fi.

## Outcome

No code is created until the device is on a local network.
