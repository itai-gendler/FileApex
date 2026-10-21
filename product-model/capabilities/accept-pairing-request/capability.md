---
availability:
- { place: android }
- { place: desktop }
domain: devices
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerIdentityRoutes.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingCoordinator.kt#PairingCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PeerAdmission.kt#PeerAdmission
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingHints.kt#PairingHints
- kind: code
  role: implementation
  target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt
---

# Accept a pairing request

On the device showing the pairing code, see who asks to join with the check code, and accept it with Codes match, pair. The two devices pair, and each device already paired with either side is introduced to the newcomer.
