---
actors:
- dj
references:
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#validateAndSetUsbRoot
- kind: code
  role: implementation
  target: vanilla-ui/components/usb/actions.mjs#promptDriveNameIfUnset
---

# Name a newly connected drive

## Goal

Connect an unnamed valid drive and give it a portable name.

## Success criterion

The prompted name is saved on the connected drive and in local device information.
