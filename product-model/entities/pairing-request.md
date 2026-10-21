---
domain: devices
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingConfirmationBoard.kt#PairingConfirmationBoard}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingHints.kt#PairingHints}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/pairing/PairingCheckCode.kt#PairingCheckCode}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/network/routes/ServerIdentityRoutes.kt}
---

# Pairing request

A device that entered or scanned a pairing code and is waiting for the device showing it to say yes.

## Information kept

- **Device name** — the name of the device asking to join.
- **Check code** — a six-digit number both screens show, worked out from both devices' keys and the pairing code; it differs if anything sits between them.
- **Hint** — what the asked device knows of the joining hardware: the same device as one already paired (a reinstall), a device removed earlier, or one that only shares a paired device's name.

## States

### Waiting

On the asked device's screen, waiting for its User to compare the codes.

### Accepted

The User said the codes match; the two devices are paired.

### Declined

The User declined, or 90 seconds passed with no answer.
