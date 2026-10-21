---
availability:
- { place: android }
- { place: desktop }
domain: devices
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/GenerateQrViewModel.kt#GenerateQrViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/LanPairingDiscovery.kt#LanPairingDiscovery
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingBeacon.kt#PairingBeacon
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/GenerateQrScreen.kt
---

# Generate a pairing code

Show a one-time pairing code on this device, as a QR code and as six digits, and announce it on the local network for a minute so another device can join.
