# paint.rs for Craft Unofficial Launcher

**An unofficial mirror** of [paint.rs](https://github.com/daijro/paint.rs) releases, maintained by
[YalKouassi](https://github.com/YalKouassi), so that
[Craft Unofficial Launcher](https://github.com/YalKouassi/craft-unofficial-launcher) can install
and update paint.rs.

This repo is **not affiliated with, endorsed by or supported by daijro** (the authors of paint.rs),
**or by ArtCraft**. Report problems with paint.rs itself upstream at
<https://github.com/daijro/paint.rs>; report problems with this mirror here.

## What this repo publishes

The packages in this repo's releases are **paint.rs's own builds**, as published on
[daijro/paint.rs's releases](https://github.com/daijro/paint.rs/releases). Nothing is rebuilt and no program file is
changed. Each release here:

- downloads upstream's packages and verifies each one before using it;
- renames them to the launcher's `<id>-<version>-<os>-<arch>` naming and, only where the launcher
  couldn't install an archive's layout, repacks that archive (the same files with the same bytes,
  in different folders);
- adds `craft-app.json`, the icon, `SHA256SUMS.txt`, and upstream's licence files from the same tag.

The notes of each release list every file, the upstream asset it came from, its SHA-256, and
whether it was repacked, so you can compare it with upstream's release.

### For paint.rs

Upstream's packages are **renamed** to the launcher's naming contract (`paint.rs-v<v>-...`
becomes `paintrs-<v>-...`; the Windows zips gain `-portable`, and `windows-x86_64` becomes
`windows-x64`) and otherwise mirrored **byte for byte**. Upstream publishes no checksum file, so downloads are checked against GitHub's own asset digests.

Not mirrored: the AVX2 and musl variants (one build per platform, the baseline one), the macOS tarballs (the launcher installs macOS apps from a `.dmg` only) and the web build.

## How it runs

[`.github/workflows/bridge.yml`](.github/workflows/bridge.yml) runs every 30 minutes. It uses
[craft-bridge](https://github.com/YalKouassi/craft-bridge) with [`bridge.toml`](bridge.toml) to
check upstream's latest release and mirror it if this repo doesn't have it yet. If upstream starts
publishing its own `craft-app.json`, the bridge stops publishing, and the launcher should point at
upstream directly.

Using this mirror means trusting its maintainer as well as upstream; see
[craft-bridge's Trust section](https://github.com/YalKouassi/craft-bridge#trust).

## Licences

paint.rs is licensed by its authors under GPL-3.0 (with a NOTICE file); each release attaches upstream's licence files.
This repo's own files (the config, workflow and this README) are available under MIT OR
Apache-2.0 ([LICENSE-MIT](LICENSE-MIT), [LICENSE-APACHE](LICENSE-APACHE)).
