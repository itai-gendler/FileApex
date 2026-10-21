---
domain: queued-files
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/db/PendingTransferEntity.kt#PendingTransferEntity}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/transfer/TransferQueueCoordinator.kt#TransferQueueCoordinator}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/presentation/TransferQueueViewModel.kt}
---

# Queued file

One send to other devices that has not reached all of them yet, listed under Queued Files with the files and the devices still waiting for them. It survives a restart of the app.

## Information kept

- **Files** — what is being sent, such as "vacation.jpg".
- **Waiting for** — the devices it has not reached yet.
- **Queued at** — when the send was made.
- **Last error** — why the last try did not finish, when it did not.

## States

### Queued

Waiting for one of its devices to answer, then sent at once.

### Sending

Being sent now.

### Paused

Stopped by the User, or held because a file changed after it was queued; it waits for Retry now.
