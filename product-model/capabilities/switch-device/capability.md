---
availability:
- { place: android }
- { place: desktop }
domain: home
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleHome.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleActiveDevice.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/domain/notifications/NotificationCompanion.kt#NotificationCompanion
---

# Switch device

Choose which paired device Home shows in the Simple layout, with Switch Device. On a computer, the chosen phone is also the one whose notifications it takes.
