# Source repositories

PenguinOS is maintained as a multi-repository Android 17 project for:

- Xiaomi Redmi Note 11 Pro 5G (`veux`)
- POCO X4 Pro 5G (`peux`)

## Entry point

Start with [android_manifest](https://github.com/GamerX65/android_manifest). Its local-manifest overlay replaces the maintained projects in a compatible AOSPA Android 17 checkout and `pinned-sources.json` records the exact upstream baselines.

## Maintained sources

- [android_device_xiaomi_veux](https://github.com/GamerX65/android_device_xiaomi_veux) — shared device tree
- [android_kernel_xiaomi_sm6375](https://github.com/GamerX65/android_kernel_xiaomi_sm6375) — SM6375 kernel
- [android_hardware_xiaomi](https://github.com/GamerX65/android_hardware_xiaomi) — Xiaomi hardware interfaces / Goodix support
- [android_hardware_qcom_thermal](https://github.com/GamerX65/android_hardware_qcom_thermal) — thermal HAL
- [android_hardware_qcom_display](https://github.com/GamerX65/android_hardware_qcom_display) — display HAL
- [android_kernel_build](https://github.com/GamerX65/android_kernel_build) — kernel-build integration
- [android_vendor_xiaomi_veux](https://github.com/GamerX65/android_vendor_xiaomi_veux) — extraction manifest and source-only patch

The maintained Android source branches use `penguinos/android-17`; metadata repositories use `main`.

## Vendor policy

The vendor repository intentionally excludes Xiaomi, Qualcomm, Goodix, APK, firmware, and shared-library blobs. Users must obtain compatible OEM firmware independently and use the included extraction metadata. This maintains source transparency without redistributing proprietary payloads.

## Transparency status

The successful release build is now represented by public source branches and a pinned manifest overlay. Base AOSPA platform revisions and local source components are recorded in the manifest repository.
