# Flashing PenguinOS on `veux`

> **Warning:** Flashing or formatting can erase data and can make a device unbootable if the wrong files are used. Verify the device codename, keep a recovery path available, and make a backup first.

This release is intended for the established `veux` fastboot-plus-custom-recovery workflow.

## Before you begin

1. Confirm the phone is the intended Xiaomi `veux` device family and its bootloader is unlocked.
2. Download every release asset and follow [VERIFY.md](VERIFY.md) before flashing.
3. Keep a known-working recovery image and a device backup available.
4. Do not flash a truncated or checksum-mismatched file.

## Typical installation flow

The following matches the maintainer-tested packaging layout. Adapt it only if your recovery/device setup requires a different established procedure.

```sh
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot flash dtbo dtbo.img
fastboot reboot recovery
```

In recovery:

1. Format data if moving from an incompatible ROM/encryption state. This **erases user data**.
2. Choose **ADB sideload**.
3. From the host, sideload the reassembled OTA:

```sh
adb sideload aospa_veux-ota.zip
```

4. Reboot system after recovery reports success.

## First boot and recovery

- First boot can take longer than normal.
- If boot fails, stop and retain recovery logs/details before repeatedly reflashing.
- Keep the exact release tag, whole OTA hash, and the flashed image hashes when reporting an issue.

## Current support boundary

The release completed host-side build, packaging, checksum, image-size, and target-files validation. It is a `userdebug/test-keys` build and has not yet been hardware boot-tested. The legacy 5.4 kernel caveat described in the release README applies.
