# EGSwitcher

A lightweight, defensive Bash utility for managing multiple Epic Games Launcher accounts on Linux/Wine. Swap accounts instantly without losing your login session or game settings.

## 🚀 Features

* **Session Persistence:** Save and load full launcher states (authentication tokens, launcher settings).
* **Defensive Design:** Automated checks for running processes to prevent data corruption.
* **WINE Native Integration:** Uses `taskkill` and `wineserver -k` for session-safe termination.
* **Smart Directory Detection:** Uses WINE registry to find the WINE user and AppData paths, with heuristic directory scanning as a fallback.

## 🛠️ Installation

1. **Move to Path:**
   Make sure the script is executable:
   `chmod +x ./epic-switcher`

2. **Configure Prefix:**
   Open the script with a text editor and ensure the `EGS_PFX` variable points to your Epic Games Launcher WINE/Proton prefix.

## 📖 Usage

### Create a New Account
    epic-switcher new <name>
1. Run: `epic-switcher new my-new-account`
2. Relaunch the Epic Launcher and login
3. Type `y` into the prompt

### Save an Active Account
    epic-switcher save [name]
1. Run:`epic-switcher save`
2. A new account prompt will appear if the active account is unknown

### Switch Accounts
    epic-switcher load <name>
1. Run:`epic-switcher load my-alt-account`
2. Launch the game

### List Saved Accounts
    epic-switcher list

### Rename an Account
    epic-switcher rename <old> <new>
&ensp; Run:`epic-switcher rename my-old-name my-new-name`

### Delete an Account
    epic-switcher delete <name>
&ensp; Run:`epic-switcher delete my-crap-account`

### See a List of Commands
    epic-switcher -h

### Show Debug Messages
    export EGS_DEBUG=1

## 🏗️ Roadmap
- Transition to user-friendly CLI configuration.

## 🛡️ Dependencies
- **WINE** or **Proton**
- **rsync**
- **coreutils**

---
Copyright © 2025 doccy-doc
**License:** GPL-3.0-only [See License](./LICENSE)

SPDX-License-Identifier: GPL-3.0-only
