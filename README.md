# Day1 - Tasks

Concise documentation of AWS EC2 Linux networking tasks, IP behavior analysis, and web server troubleshooting.

---

## Task Summary

* **TASK 1 - Linux IP Investigation**: SSHed into the Amazon Linux 2023 instance (`54.167.32.158`)[cite: 5]. Identified active interface `ens5` with private IP `172.31.24.230/20`, gateway `172.31.16.1`, and DNS server `172.31.0.2`[cite: 5].
* **TASK 2 - IPv4 Address Analysis**: Verified host IP `172.31.24.230` and confirmed internet connectivity via `ping` to `8.8.8.8` and `1.1.1.1`[cite: 5]. Classified `172.31.24.230` as a Private IPv4 address (RFC 1918 Class B)[cite: 5].
* **TASK 3 - Dynamic IP Investigation**: Tested IP behavior across an EC2 stop/start cycle using AWS metadata (`169.254.169.254`)[cite: 5]. The public IP changed from `54.167.32.158` to `54.82.54.179`, while the private IP (`172.31.24.230`) remained unchanged[cite: 5].
* **TASK 4 - Cloud Linux Server & IP Scripting**: Executed automated shell commands to pull network metadata[cite: 5]. Output confirmed interface `ens5`, private IP `172.31.24.230`, and public IP `54.82.54.179`[cite: 5].
* **TASK 5 - Cloud Network Troubleshooting**: Installed and enabled Apache (`httpd`)[cite: 5]. Confirmed service status (`active/running`) and listening port (`*:80`) via `sudo ss -tuln`[cite: 5]. Resolved connectivity blockage by allowing HTTP (Port 80) in the AWS EC2 Security Group, successfully rendering **"It works!"** at `http://54.82.54.179`[cite: 5].

---

## Quick Reference Commands

| Action | Command |
| :--- | :--- |
| **Check Network Interfaces** | `ip addr show`[cite: 5] |
| **Check Routing Table** | `ip route show`[cite: 5] |
| **Show Private IP** | `hostname -I`[cite: 5] |
| **Fetch AWS Public IP** | `curl http://169.254.169.254/latest/meta-data/public-ipv4`[cite: 5] |
| **Check Active Ports** | `sudo ss -tuln \| grep :80`[cite: 5] |
| **Service Status** | `sudo systemctl status httpd`[cite: 5] |
