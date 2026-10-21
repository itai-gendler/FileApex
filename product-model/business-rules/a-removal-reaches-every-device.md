---
appliesTo:
- type: capability
  id: remove-paired-device
- type: capability
  id: leave-cluster
- type: entity
  id: paired-device
  effect: changes
  to: Removed
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingCoordinator.kt#PairingCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/RemovalCatchUp.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/reset/ClusterResetManager.kt#ClusterResetManager
---

# Removing a device removes it on every paired device

A device removed on one device, or one that leaves the group with a wipe, is removed on every other device it reaches, and devices that missed it catch up the next time they meet. The removed device keeps its own data; the others no longer answer it, and only pairing again brings it back. A device reinstalled on the same hardware replaces its old entry the same way.
