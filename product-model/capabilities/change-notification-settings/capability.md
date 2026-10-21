---
availability:
- { place: android }
- { place: desktop }
domain: notifications
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsNotificationsPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/SettingsViewModel.kt
---

# Change notification settings

Choose in Settings → Notifications which events raise a notification on this device: Bulletin Board messages, received files and, on Android, the live transfer capsule; on Windows, whether the connected phone's notifications pop up.
