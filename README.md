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

## Automated Updates & Dual-Source Verification

This repository is monitored by a [GitHub Actions workflow](.github/workflows/update-aur.yml) with rigorous integrity checks:
1. Polls upstream releases on [GnosiWorks/Kryfo](https://github.com/GnosiWorks/Kryfo) every 6 hours.
2. **Dual-source checksum verification:** Fetches the SHA-256 hash from both the GitHub Release (`SHA256SUMS-linux`) **and** the official Kryfo web server ([kryfo.app/download](https://kryfo.app/download)), requiring 100% consensus before updating.
3. Updates `PKGBUILD` and regenerates `.SRCINFO` in a clean Arch Linux container.
4. Pushes changes to this repository and synchronizes with the AUR under protected environment review.

---

## Security & Permissions

* Binaries are packaged directly from official releases published by the Kryfo developers.
* Application files are installed in `/opt/kryfo/` and run under standard unprivileged user permissions.
* The Linux application has Tor built in and manages its own onion services directly.
* User databases, encryption keys, and secrets reside exclusively in `$HOME/.local/share/kryfo/` with user-only permissions (`0700`).

---

## License

GPL-3.0-or-later — See [LICENSE](LICENSE) for details.
