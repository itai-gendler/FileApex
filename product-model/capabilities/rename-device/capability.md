---
availability:
- { place: android }
- { place: desktop }
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/device/DeviceNameCoordinator.kt#DeviceNameCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesRenameRemoveActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsDeviceNamePage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerWriteGate.kt
---

# Rename a device

Give a device a new name, either another device from its options on Devices or this device from Settings → Device Name. A paired device that is renamed takes the name as its own, and every device learns it.
