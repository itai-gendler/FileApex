---
entities:
- entity: device-file
  shows:
  - Name
- entity: paired-device
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: macos/ShareExtension/ShareViewController.swift
- kind: code
  role: implementation
  target: macos/Shared/DevicePickerView.swift
---

# Share with FileApex

The picker Finder and the macOS Share menu open: the shared files and the paired devices to send them to.
