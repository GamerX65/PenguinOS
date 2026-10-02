# Download and verify

GitHub Release assets are CDN-backed. The OTA is split into numbered parts because the complete ZIP exceeds GitHub's single-asset size limit.

## Download

Download the following assets from the release page:

- `aospa_veux-ota.zip.part-00`
- `aospa_veux-ota.zip.part-01`
- `boot.img`
- `vendor_boot.img`
- `dtbo.img`
- `SHA256SUMS.txt`
- `release-manifest.json`

Command-line download with GitHub CLI:

```sh
gh release download v17.0-20261002-veux-userdebug \
  --repo GamerX65/PenguinOS \
  --pattern 'aospa_veux-ota.zip.part-*' \
  --pattern 'boot.img' \
  --pattern 'vendor_boot.img' \
  --pattern 'dtbo.img' \
  --pattern 'SHA256SUMS.txt' \
  --pattern 'release-manifest.json'
```

## Verify downloaded assets

From the directory containing the downloaded files:

```sh
sha256sum -c --ignore-missing SHA256SUMS.txt
```

All downloaded parts and images must report `OK` before reassembly.

## Reassemble and verify the OTA

```sh
cat aospa_veux-ota.zip.part-* > aospa_veux-ota.zip
sha256sum -c SHA256SUMS.txt
unzip -t aospa_veux-ota.zip
```

The final whole-OTA SHA-256 must be:

```text
74332a088beb7deeb4900b80dd0f75450abb985e2062f8bfeb32ae50a7fd7a82
```

Do not sideload until the whole-OTA hash and ZIP integrity test both pass.
