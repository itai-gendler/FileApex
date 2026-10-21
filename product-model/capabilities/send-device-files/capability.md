---
availability:
- { place: android }
- { place: desktop }
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferQueueCoordinator.kt#TransferQueueCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferManager.kt#TransferManager
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/MultiCopyBroadcastEngine.kt#MultiCopyBroadcastEngine
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/explorer/ExplorerCopyActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/devices/DevicesDropActions.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/ShareSendViewModel.kt#ShareSendViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerFileRoutes.kt
- kind: code
  role: implementation
  target: macos/ShareExtension/ShareViewController.swift
---

# Send files to devices

Send files and folders to one or more paired devices at once, with Send To from Local Files or another device's folders, by dropping them on a device, or from the system Share sheet, Finder or the menu bar. Every send to another device goes through Queued Files, so a device that cannot be reached gets it when it is back.
