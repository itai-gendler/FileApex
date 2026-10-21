---
domain: home
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationSyncModels.kt#NotificationPayload}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationInbox.kt#NotificationInbox}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationThreads.kt#NotificationThreads}
---

# Phone notification

A notification an Android phone shares with a computer. The computer holds it in memory while it runs, never on disk, and drops it when the phone clears it.

## Information kept

- **App** — the app that posted it.
- **Category** — Messages, Emails or Other Notifications.
- **From** — the sender or group chat for a message, the app otherwise.
- **Title** — the notification's title.
- **Text** — its text, with the recent lines of a conversation.
- **Can reply** — whether the phone can fill in its reply box.
- **Posted at** — when the phone posted it.
