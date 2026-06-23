# 🛡️ Enterprise RHEL 10 Hardening Playbook & Methodology

This repository serves as a **Technical Documentation and Security Playbook** detailing the step-by-step methodology applied to harden a Red Hat Enterprise Linux (RHEL) 10 environment. The entire configuration is aligned with industry-standard security frameworks (CIS Benchmarks) to ensure host-based security and minimize attack surfaces.

---

## 🎯 Overview & Scope

The objective of this hands-on lab was to transform a standard minimal RHEL 10 installation into a production-ready, highly secure server. Each security control was systematically evaluated, tested, and documented manually to establish a solid baseline methodology and ensure a deep architectural understanding of system internals, PAM stacks, and kernel parameters before transitioning to full automation.

---

## 🛠️ Technical Implementations & Key Skills

* **System Baseline & Standards:** Analyzed and aligned system configurations with the CIS Benchmark framework for enterprise RHEL 10 security compliance.
* **Secure Remote Access (SSH Hardening):** Enforced Ed25519 public-key-only authentication, disabled root login, relocated the default SSH port, and restricted cryptographic parameters to strong, modern ciphers/MACs.
* **Network & Firewall Hardening:** Configured stateful firewall zones using Firewalld with a default-drop policy and rate-limited rich rules. Tuned kernel network stack parameters via `sysctl` to mitigate common network attacks (e.g., enabling SYN cookies, disabling ICMP redirects).
* **Mandatory Access Control (MAC):** Maintained SELinux in Enforcing mode, managed file contexts and booleans, analyzed AVC denials, and generated custom policy modules using `audit2allow` and `semanage`.
* **Auditing & Integrity Monitoring:** Implemented system auditing via `auditd` with custom rules to monitor privilege escalation and sensitive file changes. Deployed `AIDE` (Advanced Intrusion Detection Environment) for continuous file integrity monitoring.
* **System-Wide Cryptography:** Enabled system-wide cryptographic controls and forced compliance with strict crypto-policies (FIPS 140-3 and FUTURE mode) to deprecate weak/outdated algorithms (such as MD5, SHA-1, and DES).
* **Attack Surface Reduction:** Minimized the host environment by disabling unnecessary system services, removing legacy network utilities (e.g., telnet, rsh), and implementing systemd service sandboxing (`PrivateTmp`, `ProtectSystem`).
* **Bootloader & Kernel Security:** Secured the GRUB2 bootloader with password protection, restricted rescue mode access, and enforced kernel-level hardening parameters including ASLR and core dump disabling.

---

## 🔍 Core Tools & Technologies Used
* **Operating System:** Red Hat Enterprise Linux (RHEL) 10
* **Compliance & Auditing:** OpenSCAP, Auditd, AIDE
* **Access Control:** SELinux, PAM (Pluggable Authentication Modules), Authselect
* **Networking:** Firewalld, Sysctl
