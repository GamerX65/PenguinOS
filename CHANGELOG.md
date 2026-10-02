# Changelog

## v17.0-20261002-veux-userdebug

Initial PenguinOS public release for `veux`.

### Included artifacts

- Split A/B OTA package, reassembled SHA-256: `74332a088beb7deeb4900b80dd0f75450abb985e2062f8bfeb32ae50a7fd7a82`
- `boot.img`
- `vendor_boot.img`
- `dtbo.img`
- SHA-256 checksum manifest and machine-readable release manifest

### Build and packaging validation

- `make otapackage -j16` completed successfully.
- OTA ZIP integrity test passed with `unzip -t`.
- Target-files package validation passed with non-kernel VINTF enforcement retained.
- Boot image build completed successfully.
- Image sizes were checked against the target partition constraints; `dtbo.img` is exactly 8 MiB.

### Important caveats

- Build type is `userdebug` and signing is `test-keys`.
- This release is not yet hardware boot-tested.
- The device kernel remains Linux 5.4; the host-side OTA kernel-FCM requirement is exempted only to package this legacy kernel. It is not a claim of runtime FCM or CTS compliance.
