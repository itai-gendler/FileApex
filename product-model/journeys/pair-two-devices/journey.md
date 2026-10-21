---
actors:
- user
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingConfirmationBoard.kt#PairingConfirmationBoard
- kind: code
  role: implementation
  target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt
---

# Pair two devices

## Goal

The User adds a new phone or computer to their devices.

## Success criterion

Both devices list each other as Paired, and the new device also has every device the other one was paired with.
