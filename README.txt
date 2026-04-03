sadp - Sadaptive Package Manager v1.0 (The Ironclad Release)
============================================================

Universal package manager wrapper with safety and interactive mode.
Supports 12+ native package managers and integrates with Flatpak,
Snap, and Nix for a seamless experience.

FEATURES
--------
- Automatic detection of native package managers:
  APT, Pacman, DNF, Zypper, XBPS, Emerge, Slackpkg, Eopkg, APK,
  Nix (user), Guix (user), Snap, Homebrew
- Smart installation: falls back to Flatpak with interactive candidate selection
- Safe removal with confirmation prompt
- Full system upgrade (native + optional Flatpak)
- System cleanup (orphan packages and cache) with low priority I/O
- Deep search across native, Flatpak, Snap, and Nix repositories
- Comprehensive logging with atomic rotation (5 MB limit)
- Dry-run and auto-yes options for scripting
- Security: PATH hardening, instance locking, input sanitization, no eval

REQUIREMENTS
------------
- Linux distribution with any supported package manager
- Bash 3.2 or newer
- Root access (sudo)
- For Flatpak support: flatpak installed and configured

INSTALLATION
------------
One-liner (recommended):
  sudo curl -L -o /usr/local/sbin/sadp https://raw.githubusercontent.com/rizkybayuu/sadp/main/sadp && sudo chmod +x /usr/local/sbin/sadp

Manual:
  1. Download the script and place it in /usr/local/sbin/
  2. Make it executable:
       sudo chmod +x /usr/local/sbin/sadp

USAGE
-----
  sadp install <package1> [package2]   → Install packages (native + Flatpak fallback)
  sadp remove <package1> [package2]    → Remove packages (with confirmation)
  sadp update                          → Upgrade the whole system (native + optional Flatpak)
  sadp search <term>                   → Search across all available sources
  sadp cleanup                         → Clean orphan packages and cache (with confirmation)
  sadp --yes <command>                 → Auto-accept all confirmations
  sadp --dry-run <command>             → Show what would be done without executing
  sadp --help                          → Display help

Examples:
  sadp install curl vim htop
  sadp remove firefox
  sadp update
  sadp search discord
  sadp --dry-run cleanup

LOGGING
-------
All activities are logged to:
  /var/log/sadp/install.log
Log files are automatically rotated when they reach 5 MB. A separate lock file
ensures safe concurrent writing. For diagnostic purposes, failed verification
output is also captured in the log.

ASSUMPTIONS
-----------
- Script must be run as root (sudo).
- Log directory (/var/log/sadp) should be on a local filesystem.
- Native package manager must be installed and functional.
- For ttyrun integration: sadp should be in PATH.

REPOSITORY STRUCTURE
--------------------
sadp/
  ├── README.txt     # This file
  ├── LICENSE        # MIT License
  └── sadp           # Main executable script

CONTRIBUTING
------------
Contributions are welcome! Please open an issue or submit a pull request.
Make sure your code follows the existing style and has been tested on at least
one distribution.

LICENSE
-------
MIT License – Copyright (c) 2026 rizkybayuu_
See LICENSE file for details.

CREDITS
-------
Author: rizkybayuu_

Special thanks to the AI assistants that helped refine, test, and polish this project:
  - DeepSeek
  - Gemini (Google)
  - Qwen (Alibaba)
  - Copilot (GitHub / OpenAI)
  - Claude

Their insights and suggestions contributed significantly to the security,
robustness, and usability of sadp.
