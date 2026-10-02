# Source and redistribution boundaries

PenguinOS follows a split-repository maintainer model for the shared Xiaomi Redmi Note 11 Pro 5G (`veux`) and POCO X4 Pro 5G (`peux`) platform rather than publishing an opaque monorepo snapshot.

## Public release hub

This repository publishes release documentation, checksums, manifests, and binary release assets. It is the authoritative place to find a release tag and its exact flash bundle.

## Planned source repositories

| Repository | Responsibility | Publication status |
| --- | --- | --- |
| `android_device_xiaomi_veux` | Device configuration, board config, sepolicy, overlays, VINTF policy | Planned |
| `android_kernel_xiaomi_sm6375` | Kernel source, defconfig and maintained compatibility patches | Planned |
| `android_vendor_xiaomi_veux` or extraction tooling | Vendor interface only; redistribution must be checked per blob/license | Not published |

Source material is not uploaded to this hub merely because it is present in a private build tree. Device and kernel repositories should retain meaningful upstream history and attribution. Proprietary vendor binaries require a separate redistribution decision.

## Current transparency status

The current release was built from a maintained private integration tree. The build command and validation record are documented in [BUILD.md](BUILD.md). Until source repositories and pinned manifests are published, this release should not be represented as publicly reproducible from this repository alone.
