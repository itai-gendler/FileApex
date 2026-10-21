---
appliesTo:
- type: capability
  id: send-device-files
- type: capability
  id: download-device-files
- type: capability
  id: open-attachment
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/platform/DownloadsPaths.kt
- kind: code
  role: implementation
  target: shared/src/androidMain/kotlin/com/fileapex/platform/DownloadsPaths.android.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferManager.kt#TransferManager
---

# Received files land in the receive folder

Files sent to a device, downloaded from another device, or opened from the Bulletin Board are saved in the receive folder: Download/FileApex on Android, the FileApex folder under Downloads on a computer. Folders keep their structure inside it.
