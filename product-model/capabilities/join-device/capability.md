---
availability:
- { place: android }
- { place: desktop }
domain: devices
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesPairingActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/JoinDeviceScreen.kt
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
  target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt
---

# Join a device with its code

On the joining device, take the other device's pairing code (filled in from its broadcast, typed, or scanned), compare a check code on both screens, enter the other device's PIN when it asks for one, and send the request for the other device to accept.
