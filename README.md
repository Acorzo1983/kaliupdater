# Kali Updater Tool

A robust and professional tool to safely update, upgrade, and clean your Kali Linux system. Designed for both interactive use and automated scripting.

Made with ❤️ by Albert C.

## Key Features
This tool goes beyond a simple script, incorporating features for safe, reliable, and flexible system maintenance.

- **Fully Automated Updates:** Perform a full update, full-upgrade, and clean with a single command.
- **Robust Error Handling:** Automatically resolves common apt issues:
  - **GPG Key Errors:** Refreshes Kali's GPG key if a NO_PUBKEY error is detected.
  - **APT/DPKG Locks:** Waits for existing apt processes to finish and can forcibly remove locks if they get stuck.
- **Dual-Mode Operation:**
  - **Interactive Menu:** An easy-to-use menu for manual operation.
  - **Command-Line Flags:** Full support for flags, making it perfect for automation and cron jobs.
- **Safe by Design:** Built with strict error checking (`set -euo pipefail`) and a cleanup routine (`trap`) to prevent leaving the system in an unstable state.
- **Dependency Verification:** Checks that all required tools (curl, gpg, etc.) are installed before running.
- **Structured Logging:** All operations are logged with timestamps and severity levels to `/var/log/kali-updater.log`.
- **Reboot Detection:** Checks if a reboot is required after an update (e.g., due to a kernel upgrade).

## Installation
Install the script and make it available system-wide with this one-liner:

```bash
wget -O updater.sh https://raw.githubusercontent.com/Acorzo1983/kaliupdater/main/updater.sh && chmod +x updater.sh && sudo mv updater.sh /usr/local/bin/updater
```

This command will:
1. Download the script.
2. Make it executable.
3. Move it to `/usr/local/bin/` (and rename it to `updater`) so you can run it from any location.

## Usage
The tool can be run in two modes: interactive or via command-line flags.

### Interactive Mode
For manual use, simply run the command with sudo. You will be presented with an easy-to-use menu.

```bash
sudo updater
```

### Non-Interactive Mode (for Automation)
Use flags to run specific tasks without user interaction. This is ideal for scripts or scheduled cron jobs.

#### Available Actions:

| Flag          | Description |
|---------------|-------------|
| `--full`      | Runs the complete update, upgrade, and clean process. |
| `--update`    | Only updates the package list (`apt-get update`). |
| `--clean`     | Cleans the system (`autoremove`, `autoclean`). |
| `--reinstall-apt` | Reinstalls core APT and Python components. |
| `--refresh-key`   | Manually refreshes the Kali GPG key. |

#### Options:

| Flag      | Description |
|-----------|-------------|
| `--force` | Forcibly kills and removes APT locks if they are stuck. |
| `-h, --help` | Displays the help message. |

#### Usage Examples:

```bash
# Perform a full update, non-interactively
sudo updater --full

# Schedule a weekly full update and force lock removal if needed (in a crontab)
0 3 * * 1 /usr/local/bin/updater --full --force
```

## Logs
All actions are logged with timestamps and severity levels to `/var/log/kali-updater.log`.

**Example Log Output:**
```
[2025-08-11 12:15:01] [INFO] =============================================
[2025-08-11 12:15:01] [INFO] Kali Updater v3.1 Initialized
[2025-08-11 12:15:01] [INFO] =============================================
[2025-08-11 12:15:02] [INFO] Checking for required dependencies...
[2025-08-11 12:15:02] [INFO] All dependencies are present.
[2025-08-11 12:15:02] [INFO] Checking for APT/DPKG locks...
[2025-08-11 12:15:02] [INFO] APT locks are clear.
[2025-08-11 12:15:03] [INFO] Updating package list...
[2025-08-11 12:15:08] [INFO] Package list updated successfully.
[2025-08-11 12:15:09] [WARN] A system reboot is required to apply all updates (kernel or other critical services).
[2025-08-11 12:15:09] [INFO] Update script finished. Log available at /var/log/kali-updater.log
```

## One-Liner Installation and Execution
To download, install, and run a full update in one command:

```bash
wget -O updater.sh https://raw.githubusercontent.com/Acorzo1983/kaliupdater/main/updater.sh && chmod +x updater.sh && sudo mv updater.sh /usr/local/bin/updater && sudo updater --full
```

## Contributing
Feel free to contribute to this project! Open an issue or submit a pull request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
