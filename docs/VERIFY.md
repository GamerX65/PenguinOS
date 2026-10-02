# Download and verify

## Normal release package

The normal user package is one complete file named `aospa_veux-ota.zip`, for Xiaomi Redmi Note 11 Pro 5G (`veux`) and POCO X4 Pro 5G (`peux`).

GitHub cannot host the 2,416,430,239-byte OTA as one asset because its per-asset limit is 2 GB. PenguinOS therefore does **not** use split OTA parts as its public installation flow. The original, complete OTA remains preserved on the build server and will be linked from a normal single-file mirror before public install distribution.

The GitHub Release remains the authoritative home for the release tag, `boot.img`, `vendor_boot.img`, `dtbo.img`, checksums, and machine-readable manifest.

## Verify the complete OTA

After downloading the single-file OTA from its linked mirror, place it beside `SHA256SUMS.txt` and run:

```sh
sha256sum -c SHA256SUMS.txt
unzip -t aospa_veux-ota.zip
```

The expected full-OTA SHA-256 is:

```text
74332a088beb7deeb4900b80dd0f75450abb985e2062f8bfeb32ae50a7fd7a82
```

Do not sideload until both commands pass.

## Verify GitHub flash images

The standalone GitHub assets can be verified with:

```sh
sha256sum -c --ignore-missing SHA256SUMS.txt
```

This validates `boot.img`, `vendor_boot.img`, and `dtbo.img` when they are in the current directory.
