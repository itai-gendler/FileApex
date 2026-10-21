---
appliesTo:
- type: capability
  id: accept-pairing-request
- type: capability
  id: join-device
- type: entity
  id: paired-device
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingCoordinator.kt#PairingCoordinator
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PeerAdmission.kt#PeerAdmission
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PeerTrustRules.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/security/PeerIntroductions.kt
---

# Pairing with one device pairs with its whole group

When two devices pair, each introduces the other to every device it is already paired with, and the newcomer gets the whole list. An introduced device is added only after the device adding it reaches it directly and it answers with the key it was introduced with; until then it is not listed, and it is never passed on further on someone else's word.

## Rationale

The README promises that devices are paired once. Pairing a new phone with any one computer makes it known to every other device without pairing it again on each.
