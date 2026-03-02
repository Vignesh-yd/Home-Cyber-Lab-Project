 Project Overview

This project demonstrates the setup of a virtualized isolated network for security testing and the execution of a successful exploit against a vulnerable target.

🛠️ Technical Stack

* **Hypervisor:** VirtualBox
* **Attacker Machine:** Kali Linux (2024/2026 Version)
* **Target Machine:** Metasploitable 2 (Linux-based)
* **Networking:** Private NAT Network (Isolated environment)

🏗️ Phase 1: Lab Architecture

1. **Network Isolation:** Created a custom NAT Network in VirtualBox to allow communication between VMs while preventing traffic from leaking to the local home network.
2. **Connectivity Test:** Verified the link using `ping`.
* *Result:* ICMP packets successfully exchanged between Kali and Metasploitable.

🔍 Phase 2: Reconnaissance

I performed a service version scan using **Nmap** to identify open ports and the specific software versions running on the target.

* **Command:** `nmap -sV [Target_IP]`
* **Key Finding:** Identified `vsftpd 2.3.4` running on Port 21. Research indicated this version contains a built-in backdoor.

⚡ Phase 3: Exploitation

Using the **Metasploit Framework (MSF)**, I leveraged the known backdoor vulnerability to gain unauthorized access.

1. **Tool:** `msfconsole`
2. **Exploit Module:** `exploit/unix/ftp/vsftpd_234_backdoor`
3. **Payload:** Standard CMD Shell.
4. **Execution:** Set `RHOSTS` to the target IP and executed the `exploit` command.

🏆 Results

* **Status:** Successfully opened a command shell session.
* **Access Level:** `root` (Administrative privileges confirmed via `whoami`).
* **Impact:** Full system compromise achieved.


