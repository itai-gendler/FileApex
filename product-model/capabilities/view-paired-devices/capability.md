---
availability:
- { place: android }
- { place: desktop }
domain: devices
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/DevicesViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/DeviceListRow.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/device/DeviceOrderCoordinator.kt#DeviceOrderCoordinator
---

# View paired devices

See every paired device on the Devices page: whether it answers now (Ready) or needs a tap to wake, when it was last seen, and which FileApex version it runs.
