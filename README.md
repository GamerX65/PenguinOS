# PenguinOS

PenguinOS is an Android custom-ROM release and maintainer hub for the Xiaomi Redmi Note 11 Pro 5G (`veux`) and POCO X4 Pro 5G (`peux`). This repository contains release documentation, integrity metadata, and links to downloadable builds. It intentionally does **not** carry a monolithic Android source checkout or proprietary blob dumps.

## Current release

| Field | Value |
| --- | --- |
| Tag | [`v17.0-20261002-veux-userdebug`](https://github.com/GamerX65/PenguinOS/releases/tag/v17.0-20261002-veux-userdebug) |
| Device | Xiaomi Redmi Note 11 Pro 5G (`veux`) and POCO X4 Pro 5G (`peux`) |
| Platform | AOSPA / Android 17 |
| Build type | `userdebug` |
| Signing | `test-keys` |
| Update package | A/B OTA |
| OTA SHA-256 | `74332a088beb7deeb4900b80dd0f75450abb985e2062f8bfeb32ae50a7fd7a82` |

The normal-user OTA is one complete `aospa_veux-ota.zip`. GitHub has a 2 GB per-asset limit, so this hub does **not** use split OTA parts as its installation path. The untouched full OTA stays on the build server and will be linked from a single-file release mirror; see [download and verification](docs/VERIFY.md). GitHub continues to carry the release metadata and standalone fastboot images.

## Source repositories

Use **[android_manifest](https://github.com/GamerX65/android_manifest)** as the source entrypoint. It contains the AOSPA Android 17 local-manifest overlay, exact upstream revisions, and the device/vendor setup notes.

| Repository | Default branch | Responsibility |
| --- | --- | --- |
| [android_device_xiaomi_veux](https://github.com/GamerX65/android_device_xiaomi_veux) | `penguinos/android-17` | Shared device tree for Xiaomi Redmi Note 11 Pro 5G (`veux`) and POCO X4 Pro 5G (`peux`) |
| [android_kernel_xiaomi_sm6375](https://github.com/GamerX65/android_kernel_xiaomi_sm6375) | `penguinos/android-17` | SM6375 kernel source and PenguinOS build compatibility fixes |
| [android_hardware_xiaomi](https://github.com/GamerX65/android_hardware_xiaomi) | `penguinos/android-17` | Xiaomi hardware interfaces, including the Goodix fingerprint extension |
| [android_hardware_qcom_thermal](https://github.com/GamerX65/android_hardware_qcom_thermal) | `penguinos/android-17` | Qualcomm thermal HAL compatibility source |
| [android_hardware_qcom_display](https://github.com/GamerX65/android_hardware_qcom_display) | `penguinos/android-17` | Qualcomm display compatibility source |
| [android_kernel_build](https://github.com/GamerX65/android_kernel_build) | `penguinos/android-17` | Device-scoped kernel-build integration |
| [android_vendor_xiaomi_veux](https://github.com/GamerX65/android_vendor_xiaomi_veux) | `main` | Public extraction manifest and source-only vendor patch; no proprietary blobs |

The repositories above preserve their upstream histories through GitHub forks where applicable. The public vendor repository deliberately contains **no** OEM blobs, firmware, APKs, JARs, or shared libraries.

## Support status

This is an initial `userdebug`/`test-keys` build. Packaging, OTA structure, image sizes, checksums, and non-kernel VINTF validation were verified on the build host. It has **not** yet been physically boot-tested on a device.

The device uses a legacy 5.4 kernel. Host-side OTA kernel-FCM requirements were intentionally exempted while non-kernel VINTF checks remain enabled. This does not establish runtime VINTF or CTS compliance; test on hardware before relying on it as a daily driver.

## Release policy

- Release assets are accompanied by SHA-256 checksums.
- The original build outputs are retained on the build server; publishing never removes them.
- GitHub is not used for a split-OTA installation flow. The single complete OTA remains preserved until a host that supports files above 2 GB is linked.
- Flash images are published separately for the established fastboot-plus-recovery workflow.
- Changes and known caveats are recorded in [CHANGELOG.md](CHANGELOG.md).

## Quick links

- [Flashing guide](docs/FLASHING.md)
- [Download and verify](docs/VERIFY.md)
- [Build record](docs/BUILD.md)
- [Source boundaries](docs/SOURCE.md)
- [Release changelog](CHANGELOG.md)
