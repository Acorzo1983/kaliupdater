# Kali Updater Tool

A simple and powerful tool to update and clean your Kali Linux system, made with ❤️ by **Albert C**.

---

## Features

- **Full Update**: Updates the package list, performs a full upgrade, and cleans unnecessary packages.
- **Update Package List Only**: Updates the package list without installing upgrades.
- **Clean System**: Removes unnecessary packages and cleans up old downloaded packages.
- **Interactive Menu**: Easy-to-use menu for selecting options.
- **Incremental Logging**: Logs all actions to `/var/log/updater.log` for easy review.
- **Reboot Notification**: Notifies if a reboot is required after updates.

---

## Installation

You can install the script with a single command:

```bash
wget -O updater https://raw.githubusercontent.com/Acorzo1983/kaliupdater/main/updater && chmod +x updater && sudo mv updater /usr/local/bin/updater
```
This will:

Download the script.

Make it executable.

Move it to /usr/local/bin/ so you can run it from anywhere.

## Usage
After installation, simply run:
```bash
sudo updater
```

You will see an interactive menu with the following options:

Full update: Update, upgrade, and clean the system.

Update package list only: Update the package list without installing upgrades.

Clean system: Remove unnecessary packages and clean up old downloaded packages.

Exit: Exit the script.

## Logs
All actions are logged to /var/log/updater.log. After each run, the script will notify you where the log is saved.

Example log output:
```bash
--- Update started on [Day & Time] ---
Updating package list...
Package list updated successfully.

Performing full upgrade...
Full upgrade completed successfully.

Removing unnecessary packages...
Unnecessary packages removed successfully.

Cleaning up old downloaded packages...
Cleanup of old packages completed.

Log saved to: /var/log/updater.log
--- Update finished on [Day & Time] ---
```
## One-Liner Installation and Execution
If you want to install and run the tool in one go, use this command:

```bash
curl -o updater https://raw.githubusercontent.com/Acorzo1983/kaliupdater/main/updater && chmod +x updater && sudo mv updater /usr/local/bin/updater && sudo updater
```

## Contributing
Feel free to contribute to this project! Open an issue or submit a pull request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

Made with ❤️ by Albert C.
