---
appliesTo:
- type: capability
  id: join-device
- type: capability
  id: accept-pairing-request
- type: capability
  id: decline-pairing-request
- type: entity
  id: paired-device
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingCheckCode.kt#PairingCheckCode
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingConfirmationBoard.kt#PairingConfirmationBoard
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerIdentityRoutes.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesPairingActions.kt
---

# A pairing is kept only after both screens show the same check code

The joining device shows a check code worked out from both devices' keys and the pairing code, and sends nothing until its User says the other screen matches. The device showing the code then shows the same number and keeps nothing about the joiner, not even the key it claims, until its own User accepts. If anything sat between the two devices, the numbers differ.
