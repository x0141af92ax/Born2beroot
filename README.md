*This project has been created as part of the 42 curriculum by rsbaa.*

# Born2beRoot

## Description

**Born2beRoot** is a System Administration project designed to introduce the fundamentals of virtualization, partitioning, and server security. The goal is to create a highly secure operating system within a Virtual Machine, implementing strict rules regarding storage, user management, and access control.

This project involves setting up a **Debian** server with the following design choices:

*   **Partitioning:** Implemented **LVM (Logical Volume Manager)** inside an **Encrypted** partition to ensure flexibility and data security.
*   **Security Policies:**
    *   **Passwords:** Strong password policy enforced (age and complexity).
    *   **Sudo:** Strict configuration for logging and execution rights.
*   **User Management:**
    *   Root login disabled via SSH.
    *   Created a user belonging to the `user42` and `sudo` groups.
*   **Services Installed:**
    *   **SSH:** Configured on port 4242.
    *   **UFW:** Firewall configured to only allow port 4242.
    *   **Cron:** Used for automating the monitoring script.

### Choice of Operating System
For this project, **Debian (Stable)** was selected.
*   **Pros:** Renowned for stability and security. It uses the `apt` package manager which is user-friendly. It is community-driven (open source), it has a large and active community.
*   **Cons:** Requires more configuration compared to user-friendlydistros like Ubuntu, Hardware drivers may need extra effort, its software versions are often behind cutting-edge releases.

## Technical Comparisons

As part of the project requirements, here is a comparison of the technologies involved:

### Debian vs Rocky Linux
*   **Debian:** community-driven and upstream for many distros like ubuntu/Mint/Kali, Uses the `apt` / `aptitude` package managers. It relies on **AppArmor** for mandatory access control. It is known for being strictly open-source.
*   **Rocky Linux:** community-driven and downstream of RHEL (Red Hat Enterprise Linux), Uses the `dnf` / `yum` package managers. It relies on **SELinux** for mandatory access control. It is known for enterprise-grade stability and long-term support.

### AppArmor vs SELinux
*   **AppArmor (Used in Debian):** Uses **Path-based** access control. It restricts programs based on file paths. It is generally considered easier to learn and configure for beginners.
*   **SELinux (Used in Rocky):** Uses **Inode based** access control. It assigns labels to every file and process. It offers more granular control but is significantly more complex to configure and troubleshoot.

### UFW vs Firewalld
*   **UFW (Uncomplicated Firewall):** A user-friendly interface for `iptables`. It simplifies firewall management with easy commands like `ufw allow 4242`. Used primarily on Debian/Ubuntu.
*   **Firewalld:** A firewall that uses "Zones" to define IPs/ports that are allowed and not allowed. It is the default for RHEL/Rocky systems.

### VirtualBox vs UTM
*   **VirtualBox:** A hosted hypervisor developed by Oracle. Runs on x86/AMD64 (Intel/AMD) systems for Windows, Linux, and older Macs.
* **UTM:** A hosted hypervisor for macOS, built for Apple Silicon (M1/M2/M3). Uses QEMU to support other CPU types.

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
    *   **Username:** `rsbaa`
    *   **Port:** Connect via SSH on port `4242`.

## Resources

**References:**
*   [Debian Administrator's Handbook](https://debian-handbook.info/)
*   [UFW Essentials](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-debian-10)
*   [SSH Configuration Manual](https://linuxgenie.net/how-to-configure-and-enable-ssh-on-debian-12/)

**AI Usage:**
AI assistance was utilized during the development of this project for the following tasks:
*   **Conceptual Understanding:** Explaining the differences between LVM layers (PV, VG, LV) and the boot process (MBR).
*   **Scripting:** Assisting with `awk` and `grep` syntax for the `monitoring.sh` script to parse system resources correctly.
*   **Troubleshooting:** Debugging syntax errors in the `pam_pwquality` configuration and resolving network issues related to SSH port forwarding.
