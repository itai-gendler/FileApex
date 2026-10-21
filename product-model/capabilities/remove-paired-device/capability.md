---
availability:
- { place: android }
- { place: desktop }
domain: devices
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesRenameRemoveActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingCoordinator.kt#PairingCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/devices/DevicesDialogs.kt
---

# Remove a device

Take a device off the paired list from its options on Devices. The removal reaches every paired device, and the removed one stays gone until it is paired again.
