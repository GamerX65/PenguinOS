# Build record

This document records the successful environment used to package the initial public `veux` release. It is an audit record, not yet a public source-reproducibility guide.

## Recorded invocation

```sh
cd /mnt/data/penguinos
export CCACHE_DIR=/mnt/data/ccache USE_CCACHE=1
. build/envsetup.sh
lunch aospa_veux-cp2a-userdebug
make otapackage -j16
```

## Successful result

```text
ota_from_target_files.py - INFO : done. out/target/product/veux/aospa_veux-ota.zip
ninja: Build Succeeded
```

## Host-side validation recorded for this release

- Full OTA packaging completed successfully.
- `unzip -t` passed for the OTA.
- OTA metadata records A/B update type and pre-device values `peux,veux`.
- Target-files validation passed while retaining non-kernel VINTF enforcement.
- `m bootimage -j16` completed successfully.
- Published `boot.img`, `vendor_boot.img`, and `dtbo.img` were recorded and checksummed.
- `dtbo.img` is exactly 8 MiB and fits the target partition size.

## Kernel compatibility caveat

The physical device kernel is Linux 5.4. Android 17 FCM host packaging requires a newer kernel version, so the build uses a device-scoped OTA kernel-requirement exemption. This permits host packaging while retaining non-kernel VINTF checks; it does not claim that the installed system is runtime FCM-7 or CTS compliant.
