---
availability:
- { place: android }
- { place: desktop }
domain: devices
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesOrderActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/device/DeviceOrderCoordinator.kt#DeviceOrderCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/DeviceOrderDragReorder.kt
---

# Reorder devices

Drag devices into the order the User wants on Devices and keep it with Done, or go back with Revert. The order is this device's own.
