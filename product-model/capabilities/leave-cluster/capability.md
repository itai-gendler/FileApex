---
availability:
- { place: android }
- { place: desktop }
domain: security-and-access-control
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/SecurityAccountScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/reset/ClusterResetManager.kt#ClusterResetManager
---

# Leave the group and wipe all data

Take this device out of the paired group for good with Leave Cluster & Wipe All Data: online devices are told to remove it, its keys and data are erased, and the app starts over as on first launch.
