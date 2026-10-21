---
singleton: true
references:
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/settings/BaseAppSettings.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/settings/PinIdleTimeout.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/data/settings/BulletinRemoteFilePurgePreference.kt}
- {kind: code, role: implementation, target: shared/src/commonMain/kotlin/com/fileapex/domain/clipboard/ClipboardShareMode.kt}
---

# Device settings

This device's own name and the choices the User made on it. Every device in the group keeps its own.

## Information kept

- **Device name** — how this device appears to the others; letters and numbers, with spaces and hyphens.
- **Require PIN** — whether other devices need this device's PIN to pair with it and to browse it. Off by default.
- **Device PIN** — the 4 to 8 digit PIN, kept only on this device.
- **Browse unlock idle timeout** — how long a PIN-protected device stays unlocked while this device browses it: Immediate, 1, 5 (the default) or 10 minutes.
- **Clipboard Sharing** — whether this device sends and takes clipboard text. Off by default.
- **Share clipboard with** — All devices or Specific devices; nothing is sent until one is chosen.
- **Clipboard devices** — the devices checked under Specific devices.
- **Automatically send** — on a computer, whether copied text is sent without pressing Send Clipboard.
- **Send Clipboard button** — on Android, a Send Clipboard button on the Server Active notification.
- **Accessibility** — on Android builds outside Google Play, whether copies made in other apps are noticed in the background.
- **Via Cellular** — on Android, whether clipboard text may also travel over the encrypted cloud relay when off Wi-Fi.
- **Bulletin Board notifications** — whether new Bulletin Board messages raise a notification here.
- **File Transfer notifications** — whether received files raise a notification here.
- **Live activity** — on Android, a floating capsule with the progress of active transfers.
- **Allow remote file deletion** — on Android, whether a Bulletin Board delete from another device may also delete the downloaded file here: not yet decided, on, or off.
- **Share notifications** — on Android, whether this phone shares its notifications.
- **Share notifications with** — the one paired device the notifications go to.
- **Verification codes** — whether notifications that contain a sign-in or verification code are shared too. Off by default.
- **Shared apps** — the apps whose notifications are shared; every app is off until turned on.
- **Sync dismissal** — whether reading a notification on the other device also clears it on the phone.
- **Notifications from connected phone** — on Windows, whether a shared notification also pops up as a Windows notification. Off by default.
- **Connected device** — in the Simple layout, the one device Home shows.
