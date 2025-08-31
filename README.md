# Linea Besu (Basic Node) - Quick Install Script

This script provides a one-line command to fully automate the installation of a **basic Linea Besu follower node**.

It handles all necessary steps, including installing dependencies (like Docker), configuring permissions, automatically setting the public IP, and starting the node as a background service. This script is designed for Debian-based Linux systems (e.g., Ubuntu).

---

## Prerequisites

-   A server running a **Debian-based OS** (e.g., Ubuntu 20.04 / 22.04 or later).
-   Root or `sudo` privileges.

---

## Installation

Run the single command below in your terminal to start the installation.

**Important**: Replace the URL with the raw link to your own `install-basic.sh` script hosted on GitHub.

```bash
curl -sSL https://raw.githubusercontent.com/codeesura/linea-node/main/install-basic.sh | bash
```

The script will handle the entire setup process, and your node will be running upon completion.

---

## Post-Installation Management

Your Linea node runs in the background inside a Docker container. All management commands should be run from the `~/linea-node` directory.

### Managing the Node

-   **Check Logs**:
    ```bash
    cd ~/linea-node && sudo docker compose logs -f
    ```

-   **Stop the Node**:

    ```bash
    cd ~/linea-node && sudo docker compose down
    ```
    
-   **Start the Node (after stopping)**:

    ```bash
    cd ~/linea-node && sudo docker compose up -d
    ```
    
### Docker Permissions

The script adds your user to the `docker` group to allow running Docker commands without `sudo`.

**Important**: For this change to take effect, you must **log out of the server and log back in**. After re-logging in, you can omit `sudo` from the commands above.

---

## Uninstallation

To completely remove the node and all its data:

1.  Stop the container and remove its data volume:

    ```bash
    cd ~/linea-node && sudo docker compose down -v
    ```
    
3.  Remove the installation directory:

    ```bash
    cd ~ && rm -rf ~/linea-node
    ```
