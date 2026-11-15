# kryfo-bin (AUR)

[![Check and Update AUR package](https://github.com/CyberPingU/kryfo-bin/actions/workflows/update-aur.yml/badge.svg)](https://github.com/CyberPingU/kryfo-bin/actions/workflows/update-aur.yml)
[![AUR version](https://img.shields.io/aur/version/kryfo-bin.svg?color=blue)](https://aur.archlinux.org/packages/kryfo-bin)
[![License: GPL-3.0-or-later](https://img.shields.io/badge/License-GPL--3.0--or--later-green.svg)](LICENSE)

Arch Linux (AUR) package for [**Kryfo Desktop**](https://kryfo.app) — Private messenger over Tor, no phone number or account.

Upstream repository: [GnosiWorks/Kryfo](https://github.com/GnosiWorks/Kryfo)

---

## Installation

> [!NOTE]
> **AUR Status (Temporary):** New account registrations on `aur.archlinux.org` are currently paused by the Arch Linux team due to automated bot waves.  
> As a result, this package is not yet indexed on the official AUR and cannot be installed via `yay`/`paru` directly. Please use the **Manual installation** method below until registrations reopen.

### Manual installation with `makepkg` (Current method)

```bash
git clone https://github.com/CyberPingU/kryfo-bin.git
cd kryfo-bin
makepkg -si
```

### Via AUR helper (Once AUR registration reopens)

```bash
yay -S kryfo-bin
# or
paru -S kryfo-bin
```

---

## Automated Updates & Integrity Checks

This repository is monitored by a [GitHub Actions workflow](.github/workflows/update-aur.yml) with multiple integrity gates:
1. Polls upstream releases on [GnosiWorks/Kryfo](https://github.com/GnosiWorks/Kryfo) every 6 hours.
2. Cross-references the version against [kryfo.app/download](https://kryfo.app/download) to confirm the release is live and intended for end users.
3. Retrieves and strictly verifies the Linux tarball checksum against the official `SHA256SUMS-linux` file published by upstream (fails immediately if unverified).
4. Updates `PKGBUILD` and regenerates `.SRCINFO` in an Arch Linux container.
5. Deploys to AUR with environment protection / review checks.

---

## Security & Permissions

* Binaries are packaged directly from official releases published by the Kryfo developers.
* Application files are installed in `/opt/kryfo/` and run under standard unprivileged user permissions.
* The Linux application has Tor built in and manages its own onion services directly.
* User databases, encryption keys, and secrets reside exclusively in `$HOME/.local/share/kryfo/` with user-only permissions (`0700`).

---

## License

GPL-3.0-or-later — See [LICENSE](LICENSE) for details.
