# sadp — Sadaptive Package Manager

> **v1.0 — The Ironclad Release**
>
> Universal package manager wrapper with safety and interactive mode.
> Supports 12+ native package managers and integrates with Flatpak, Snap, and Nix for a seamless experience.

---

## Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Logging](#logging)
- [Repository Structure](#repository-structure)
- [Contributing](#contributing)
- [License](#license)
- [Credits](#credits)

---

## Features

- **Auto-detection** of native package managers:
  `APT`, `Pacman`, `DNF`, `Zypper`, `XBPS`, `Emerge`, `Slackpkg`, `Eopkg`, `APK`, `Nix (user)`, `Guix (user)`, `Snap`, `Homebrew`
- **Smart installation** — falls back to Flatpak with interactive candidate selection
- **Safe removal** with confirmation prompt
- **Full system upgrade** (native + optional Flatpak)
- **System cleanup** — orphan packages and cache with low-priority I/O
- **Deep search** across native, Flatpak, Snap, and Nix repositories
- **Comprehensive logging** with atomic rotation (5 MB limit)
- **Dry-run and auto-yes** options for scripting
- **Security** — PATH hardening, instance locking, input sanitization, no `eval`

---

## Requirements

| Requirement | Notes |
|---|---|
| Linux (any distro) | Any supported package manager must be present |
| Bash | Version 3.2 or newer |
| Root access | via `sudo` |
| Flatpak (optional) | Required only for Flatpak fallback support |

---

## Installation

**One-liner (recommended):**

```bash
sudo curl -L -o /usr/local/sbin/sadp \
  https://raw.githubusercontent.com/rizkybayuu/sadp/main/sadp \
  && sudo chmod +x /usr/local/sbin/sadp
```

**Manual:**

```bash
# 1. Download the script
curl -L -o sadp https://raw.githubusercontent.com/rizkybayuu/sadp/main/sadp

# 2. Move to system path and make executable
sudo mv sadp /usr/local/sbin/sadp
sudo chmod +x /usr/local/sbin/sadp
```

---

## Usage

```
sadp install <package1> [package2]   Install packages (native + Flatpak fallback)
sadp remove  <package1> [package2]   Remove packages (with confirmation)
sadp update                          Upgrade the whole system (native + optional Flatpak)
sadp search  <term>                  Search across all available sources
sadp cleanup                         Clean orphan packages and cache (with confirmation)
sadp --yes   <command>               Auto-accept all confirmations
sadp --dry-run <command>             Show what would be done without executing
sadp --help                          Display help
```

**Examples:**

```bash
sadp install curl vim htop
sadp remove firefox
sadp update
sadp search discord
sadp --dry-run cleanup
```

---

## Logging

All activity is logged to `/var/log/sadp/install.log`.

- Log files are automatically rotated at **5 MB**
- A separate lock file ensures safe concurrent writes
- Failed verification output is also captured for diagnostics

> **Note:** The log directory (`/var/log/sadp`) should reside on a local filesystem.

---

## Repository Structure

```
sadp/
├── README.md     # This file
├── LICENSE       # MIT License
└── sadp          # Main executable script
```

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.
Ensure your code follows the existing style and has been tested on at least one distribution.

---

## License

MIT License — Copyright © 2026 [rizkybayuu\_](https://github.com/rizkybayuu)
See [LICENSE](./LICENSE) for details.

---

## Credits

**Author:** [rizkybayuu\_](https://github.com/rizkybayuu)

Special thanks to the AI assistants that helped refine, test, and polish this project:

- [DeepSeek](https://www.deepseek.com)
- [Gemini](https://gemini.google.com) (Google)
- [Qwen](https://qwenlm.github.io) (Alibaba)
- [Copilot](https://github.com/features/copilot) (GitHub / OpenAI)
- [Claude](https://claude.ai) (Anthropic)

Their insights and suggestions contributed significantly to the security, robustness, and usability of sadp.
