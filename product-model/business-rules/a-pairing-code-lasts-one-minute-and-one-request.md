---
appliesTo:
- type: capability
  id: generate-pairing-code
- type: capability
  id: join-device
- type: entity
  id: pairing-code
  effect: changes
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/LanPairingDiscovery.kt#LanPairingDiscovery
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingBeacon.kt#PairingBeacon
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerIdentityRoutes.kt
---

# A pairing code lasts one minute and answers one request

A code is broadcast for one minute after it is generated. The first request that is accepted or declined, or left unanswered, ends it, and each new code differs from the last one used. Leaving the Generate QR Code screen stops the broadcast.
