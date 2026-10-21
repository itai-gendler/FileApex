---
availability:
- { place: android }
- { place: desktop }
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsClipboardPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/ui/settings/SettingsClipboardShareTargetsPage.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/com/fileapex/presentation/SettingsViewModel.kt
- kind: code
  role: implementation
  target: composeApp/src/commonMain/kotlin/com/fileapex/App.kt
---

# Change clipboard settings

Turn clipboard sharing on or off in Settings → Clipboard, choose All devices or Specific devices under Share clipboard with, and set how copies are noticed: Automatically send on a computer; the Send Clipboard notification button, Accessibility and Via Cellular on Android.
