---
availability:
- { place: android }
- { place: desktop }
domain: devices
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesConnectActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/ExplorerViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/browse/BrowserCoordinator.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerFileRoutes.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/session/DeviceSessionManager.kt
---

# Browse a device's files

Open another device from Devices (or Browse on Home) and move through its folders from its browsable root, entering its PIN first when it asks for one.
