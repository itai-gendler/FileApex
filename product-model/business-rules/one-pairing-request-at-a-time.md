---
appliesTo:
- type: capability
  id: accept-pairing-request
- type: capability
  id: decline-pairing-request
- type: entity
  id: pairing-request
  effect: changes
  to: Declined
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingConfirmationBoard.kt#PairingConfirmationBoard
---

# A device answers one pairing request at a time, for 90 seconds

While a request is on screen waiting for an answer, another device that asks is told the device is already pairing with someone. A request nobody answers within 90 seconds counts as declined.
