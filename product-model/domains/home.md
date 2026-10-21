---
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/ui/adaptive/SimpleHome.kt}
---

# Home

Home in the Simple layout, the default: one connected device at a time, with its overview, its clipboard sharing and, on a computer, the connected phone's notifications.

## Boundary

This domain does not own the phone's choice of which apps it shares; that is the phone's Broadcast Notifications setting.
