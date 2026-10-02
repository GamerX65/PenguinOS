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

## Repository boundaries

Maintainer projects are deliberately separated so history, licensing, review, and downstream contributions remain clear:

- **`PenguinOS`** — public release hub, documentation, release metadata, checksums, and signed build assets.
- **Device tree** — planned as `android_device_xiaomi_veux`; device configuration and VINTF/board policy only.
- **Kernel tree** — planned as `android_kernel_xiaomi_sm6375`; upstream/source history and device kernel patches only.
- **Vendor materials** — proprietary blobs are not committed to this public hub. A future vendor repository, if published, will contain only materials that can be redistributed lawfully or extraction scripts/manifest metadata.

This separation is intentional. A release asset is not a source drop, and a source repository should not hide proprietary binaries among otherwise reviewable code. The current source-publication status and recorded build environment are documented in [SOURCE](docs/SOURCE.md) and [BUILD](docs/BUILD.md).

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
