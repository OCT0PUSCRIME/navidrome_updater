# Navidrome Update Script

This script automates the process of updating Navidrome on a Linux system. It simplifies the installation or update process by fetching the latest version or a user-specified version, extracting the files, setting proper permissions, and restarting the Navidrome service.

## Features

- Checks for the existence of a `.env` file and loads environment variables from it.
- Prompts the user to create a `.env` file if it doesn't exist, asking for:
  - Navidrome user
  - Navidrome group
  - Installation location (default: `/opt/navidrome`)
- Fetches the latest Navidrome release version or allows manual version input.
- Downloads the selected version and installs it to the specified location.
- Sets appropriate ownership and permissions.
- Restarts the Navidrome service after updating.

## Prerequisites

- `sudo` access on the system.
- `wget`, `tar`, and `curl` installed.

## Usage

1. Clone or copy the script to your system.
2. Make the script executable:
   ```bash
   chmod +x navidrome_update.sh
   ```
3. Run the script with `sudo`:
   ```bash
   sudo ./navidrome_update.sh
   ```

## Environment Variables

The script uses a `.env` file to store configuration variables. If the file doesn't exist, it will prompt the user to create one. Example `.env` file:

```plaintext
ND_USER=navidrome_user
ND_GROUP=navidrome_group
ND_INSTALL_LOCATION=/opt/navidrome
```

## Workflow

1. The script checks for or creates the `.env` file.
2. Prompts the user for the version to install:
   - Fetches the latest version from GitHub if selected.
   - Allows manual version input (e.g., `v0.48.0`).
3. Downloads the appropriate `.tar.gz` file from GitHub.
4. Extracts the archive to the specified installation directory.
5. Sets ownership and permissions for the Navidrome files.
6. Restarts the Navidrome service using `systemctl`.

## Example

```bash
$ sudo ./navidrome_update.sh
Loading variables from .env.
Do you want the latest version? (y/n): y
Fetching latest version...
Selected version: v0.48.0
Downloading https://github.com/navidrome/navidrome/releases/download/v0.48.0/navidrome_0.48.0_linux_amd64.tar.gz...
Extracting Navidrome to /opt/navidrome...
Setting executable permissions on /opt/navidrome/navidrome...
Setting ownership to navidrome_user:navidrome_group...
Cleaning up temporary files...
Restarting Navidrome service...
Update complete!
```

## License

This script is provided as-is under the [MIT License](https://opensource.org/licenses/MIT).

## Contributing

Feel free to open issues or submit pull requests to improve the script.
