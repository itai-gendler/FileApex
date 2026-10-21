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
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingConfirmationBoard.kt#PairingConfirmationBoard
- kind: code
  role: implementation
  target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt
---

# Decline a pairing request

On the device showing the pairing code, turn down a device that asks to join, with Decline. The code is spent: pairing again needs a new one.
