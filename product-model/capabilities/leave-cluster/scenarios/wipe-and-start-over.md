---
kind: primary
routes:
  android: Android app
  desktop: Desktop app
steps:
- text: "The User chooses Leave Cluster & Wipe All Data, then Continue to Wipe"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
- text: "The User confirms with Wipe All Data & Reset"
  kind: actor
  actor: user
  entities: []
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
- text: "The Product tells every online paired device to remove this one"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: reads, facts: [Address, Online] }
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
- text: "The Product erases this device's keys, its list of devices, its board and its settings, and signs it out of Tailscale"
  kind: product
  actor: user
  entities:
  - { entity: paired-device, effect: changes, from: Paired, to: Removed, facts: [] }
  - { entity: bulletin-message, effect: removes, from: Posted }
  - { entity: device-settings, effect: changes, facts: [Device name, Require PIN, Device PIN, Clipboard Sharing, Share notifications] }
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
- text: "The Product says all data was removed and returns to the first-launch screen"
  kind: product
  actor: user
  entities: []
  contexts:
    android:
      place: android::leave-cluster
    desktop:
      place: desktop::leave-cluster
---

# Wipe and start over

## Trigger

The device is being given away, or the User wants a clean start.

## Outcome

This device is out of the group and holds nothing from it; online devices have removed it.
