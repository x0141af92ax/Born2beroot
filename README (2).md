*This project has been created as part of the 42 curriculum by rsbaa.*

# Born2beRoot

## Description

**Born2beRoot** is a System Administration project designed to introduce the fundamentals of virtualization, partitioning, and server security. The goal is to create a highly secure operating system within a Virtual Machine, implementing strict rules regarding storage, user management, and access control.

This project involves setting up a **Debian** server with the following design choices:
*   **Virtualization:** Created using VirtualBox.
*   **Partitioning:** Implemented **LVM (Logical Volume Manager)** inside an **Encrypted** partition to ensure flexibility and data security.
*   **Security:**
    *   **SSH:** Configured on port 4242 with Root login disabled.
    *   **Firewall:** UFW configured to only allow necessary connections.
    *   **Passwords:** Strong password policy enforced (age and complexity).
    *   **Sudo:** Strict configuration for logging and execution rights.
*   **Automation:** A monitoring script broadcasts system information every 10 minutes using Cron.

### Choice of Operating System
For this project, **Debian (Stable)** was selected.
*   **Pros:** Renowned for stability and security. It uses the `apt` package manager which is widely supported and user-friendly. It is community-driven (open source).
*   **Cons:** "Stable" releases often feature older software versions compared to rolling-release distributions.

## Technical Comparisons

As part of the project requirements, here is a comparison of the technologies involved:

### Debian vs Rocky Linux
*   **Debian:** Uses the `.deb` package format and the `apt` / `aptitude` package managers. It relies on **AppArmor** for mandatory access control. It is known for being strictly open-source.
*   **Rocky Linux:** A downstream binary compatible clone of RHEL (Red Hat Enterprise Linux). It uses `.rpm` packages and the `dnf` / `yum` package managers. It relies on **SELinux** for security. It is more common in corporate/enterprise environments.

### AppArmor vs SELinux
*   **AppArmor (Used in Debian):** Uses **Path-based** access control. It restricts programs based on file paths. It is generally considered easier to learn and configure for beginners.
*   **SELinux (Used in Rocky):** Uses **Inode/Label-based** access control. It assigns labels to every file and process. It offers more granular control but is significantly more complex to configure and troubleshoot.

### UFW vs Firewalld
*   **UFW (Uncomplicated Firewall):** A user-friendly interface for `iptables` (or `nftables`). It simplifies firewall management with easy commands like `ufw allow 4242`. Used primarily on Debian/Ubuntu.
*   **Firewalld:** A dynamic firewall manager that uses "Zones" to define trust levels for network connections. It is the default for RHEL/Rocky systems.

### VirtualBox vs UTM
*   **VirtualBox:** A type-2 hypervisor developed by Oracle. It is the industry standard for x86/AMD64 architectures (Intel/AMD chips) on Windows, Linux, and older Macs.
*   **UTM:** A virtualization software for macOS, particularly optimized for **Apple Silicon (M1/M2/M3)**. It uses QEMU under the hood to emulate or virtualize different architectures.

## Instructions

Since this is a System Administration project, there is no source code to compile. To evaluate this project:

1.  **Clone the repository:**
    ```bash
    git clone <repository_url>
    ```
2.  **Verify the Signature:**
    Compare the hash in `signature.txt` with the Virtual Machine's disk file (`.vdi`).
    *   *Windows Command:* `certUtil -hashfile rsbaa42.vdi sha1`
    *   *Linux Command:* `sha1sum rsbaa42.vdi`
3.  **Launch the VM:**
    Open the `.vdi` file in VirtualBox.
4.  **Log In:**
    *   **Username:** `rsbaa` or `root`
    *   **Port:** Connect via SSH on port `4242`.

## Resources

**References:**
*   [Debian Administrator's Handbook](https://debian-handbook.info/)
*   [UFW Essentials](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-debian-10)
*   [SSH Configuration Manual](https://man.openbsd.org/sshd_config)

**AI Usage:**
AI assistance was utilized during the development of this project for the following tasks:
*   **Conceptual Understanding:** Explaining the differences between LVM layers (PV, VG, LV) and the boot process (MBR vs GPT).
*   **Scripting:** Assisting with `awk` and `grep` syntax for the `monitoring.sh` script to parse system resources correctly.
*   **Troubleshooting:** Debugging syntax errors in the `pam_pwquality` configuration and resolving network issues related to SSH port forwarding.