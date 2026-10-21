---
kind: edge
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User taps a device marked Tap to wake"
  kind: actor
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Name, Online, Last seen] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product sends a wake signal on the local network and tries every route it knows"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Address] }
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The device still does not answer"
  kind: condition
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
- text: "The Product says it could not reach the device, and to check that FileApex runs on it and both are on the same network"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::devices
    desktop:
      place: desktop::devices
---

# The device does not answer

## Trigger

The other device is asleep, closed or on another network.

## Outcome

Nothing opens; the device stays marked Tap to wake.

## Edge cases

- With this device off Wi-Fi and no other route, the Product asks to connect to Wi-Fi or Ethernet first.
