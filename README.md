# EGSwitcher

A lightweight, defensive Bash utility for managing multiple Epic Games Launcher accounts on Linux/Wine. Swap accounts instantly without losing your login session or game settings.

## 🚀 Features

* **Session Persistence:** Save and load full launcher states (authentication tokens, launcher settings).
* **Defensive Design:** Automated checks for running processes to prevent data corruption.
* **WINE Native Integration:** Uses `taskkill` and `wineserver -k` for session-safe termination.
* **Smart Directory Detection:** Uses WINE registry to find the WINE user and AppData paths, with heuristic directory scanning as a fallback.
* **User Friendly CLI Config:** Users can choose to edit a config file or use the CLI to modify the config.

## 🛠️ Installation

1. **Make Executable:**
   chmod +x ./epic-switcher

2. **Add to Path (Optional):**
   mv ./epic-switcher ~/.local/bin/

3. **Configure Prefix:**
   epic-switcher config pfx
   (Provide the full path to your Epic Games Launcher WINE/Proton prefix).

## 📖 Usage

### Create a New Account
    epic-switcher new <name>
1. `epic-switcher new my-new-account`
2. Relaunch the Epic Launcher and login
3. Type `y` into the prompt

### Save an Active Account
    epic-switcher save [name]
- Run: `epic-switcher save my-account`
- Or run: `epic-switcher save` and follow the prompt if required

### Switch Accounts
    epic-switcher load <name>
1. Run: `epic-switcher load my-alt-account`
2. Launch the game

### List Saved Accounts
    epic-switcher list

### Rename an Account
    epic-switcher rename <old> <new>
- Run: `epic-switcher rename my-old-name my-new-name`

### Delete an Account
    epic-switcher delete <name>
- Run: `epic-switcher delete my-crap-account`

### Change the Active Prefix
    epic-switcher config pfx [/path/to/prefix]
For persistent change:
- Run: `epic-switcher config pfx` and follow the prompt
- Or run: `epic-switcher config pfx "/home/username/.wine/"`

To change for a single run:
- Run: `EGSPFX="/path/to/prefix" epic-switcher [command]`
    
### See a List of Commands
    epic-switcher -h|--help
- Run: `epic-switcher`
- Or run: `epic-switcher -h`
- Or run: `epic-switcher --help`

### Show Debug Messages
To enable for a single run:
- Run: `EGSDEBUG=1 epic-switcher [command]`

To enable persistent debugging:
- Run: `epic-switcher config debug 1`
- Or edit `~/.config/egswitcher/egswitcher.conf`: `EGS_DEBUG=1`

## 📁 File Schema
EGSwitcher follows the **XDG Base Directory Specification**. All files and directories are created automatically as required. If you wish to backup or inspect your data, they are located here:

* **Account Data:** `$XDG_DATA_HOME/egswitcher/`
    *(Defaults to `~/.local/share/egswitcher/`)*
* **Config Files:** `$XDG_CONFIG_HOME/egswitcher/`
    *(Defaults to `~/.config/egswitcher/`)*
* **Cache/Temp Files:** `$XDG_CACHE_HOME/egswitcher/`
    *(Defaults to `~/.cache/egswitcher/`)*

> [!TIP]
> If these environment variables are not set on your system, it falls back to the standard hidden directories in your `$HOME`.

## 🛡️ Dependencies
- **WINE** or **Proton**
- **rsync**
- **coreutils**

---
Copyright © 2025 doccy-doc
**License:** GPL-3.0-only [See License](./LICENSE)

SPDX-License-Identifier: GPL-3.0-only
