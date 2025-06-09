# Windows Software Update Script (using winget)

This PowerShell script automates checking for and installing software updates on Windows using the `winget` command-line package manager.

## Features

* **`winget` availability check:** Verifies if `winget` is installed and accessible on your system.
* **List upgradable packages:** Displays a list of all software with available updates through `winget`.
* **Selective or all upgrades:** Allows you to choose between upgrading all detected packages, specific packages by their ID, or skipping the update process entirely.
* **Silent upgrades:** Attempts to install updates silently to minimize user interaction.
* **Error handling:** Provides feedback for common issues, such as `winget` not being found or upgrade failures.

## Prerequisites

* **Windows 10 (version 1709 or later) or Windows 11:** `winget` is typically pre-installed or available for these versions.
* **`winget` (Windows Package Manager) installed:**
    * You can get it from the Microsoft Store (search for "App Installer").
    * Alternatively, it often comes bundled with Windows updates.
    * Ensure `winget.exe` is in your system's PATH environment variable.
* **PowerShell 5.1 or newer:** This script is written in PowerShell.

## How to Use

1.  **Save the script:** Save the provided PowerShell code into a `.ps1` file (e.g., `Update-Software.ps1`).

2.  **Open PowerShell:**
    * Search for "PowerShell" in the Start Menu.
    * **Recommended:** Run PowerShell as an **Administrator** for the best chance of successful updates, as many applications require administrative privileges to install or update.

3.  **Navigate to the script directory:** Use the `cd` command to go to the directory where you saved the `Update-Software.ps1` file.
    ```powershell
    cd C:\Path\To\Your\Script
    ```

4.  **Execute the script:**
    ```powershell
    .\Update-Software.ps1
    ```

### Script Flow:

1.  The script will first check for `winget`'s presence.
2.  It will then list all detected upgradable packages.
3.  You will be prompted to choose an action:
    * Type `all` to upgrade all listed packages.
    * Type a comma-separated list of package IDs (e.g., `Google.Chrome,Microsoft.Edge`) to upgrade specific ones.
    * Type `n` to skip the update process.
4.  The script will proceed with your chosen action and provide status messages.

## Important Notes

* **User Account Control (UAC):** You may receive UAC prompts during the script's execution, especially if `winget` requires elevation to perform an update. This is normal; grant permission when prompted.
* **Silent Installation:** The script uses `--silent` and `--accept-package-agreements --accept-source-agreements` flags for `winget upgrade`. While this tries to automate the process, some applications might still require manual intervention during their upgrade process.
* **Application in Use:** If an application is currently running, `winget` might fail to upgrade it. Close any applications before running the script for smoother updates.
* **Troubleshooting `winget`:** If `winget` isn't found or consistently fails, ensure it's correctly installed and its path is set. You might need to update your Windows OS or reinstall the App Installer from the Microsoft Store.
* This script updates software managed by `winget`. It does **not** manage Windows OS updates or updates from other package managers or proprietary updaters.

## License

This script is provided "as-is" without any explicit license. Feel free to modify and distribute it as needed.
