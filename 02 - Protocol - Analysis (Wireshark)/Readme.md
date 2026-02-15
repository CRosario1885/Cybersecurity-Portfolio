# [Project Name: Network Traffic Analysis & Protocol Hardening]

## 📝 Executive Summary
**Objective:** To intercept and analyze unencrypted network traffic between a client and server to identify security vulnerabilities.
**Outcome:** Successfully captured plaintext credentials (username and password) using Wireshark, demonstrating the critical risk of using legacy protocalls like Telnet.

## 🛠️ Environment & Tools
* **Attacker Machine:** Kali Linux (IP: 10.0.2.4)
* **Victum Machine:** Metasploitable 2 (IP: 10.0.2.5)
* **Tools:** Wireshark, Telnet Client
* **Network:** Isolated VirtualBox Nat Network

## 🏗️ Lab Topology
**Step-by-Step Methodology**
1. Listener Setup: Launched Wireshark on the Kali machine and began capturing packets on the eth0 interface.
2. Traffic Generation: Initiated a Telnet connection from the Kali terminal to the Metasploitable server: telnet 10.0.2.5.
3. Authentication: Logged into the vicim machine using known default credentials (msfadmin/msfadmin).
4. Protocol Filtering: Applied a display filter (telnet) in Wireshark to isolate the relevant traffic from background noise.
5. Stream Reconstruction: Used the "Follow TCP Stream" feature to view the conversation in a human-readable format.


## 📊 Findings & Evidence
**Vulnerability:** The Telnet protocol transmits data in cleartext.
[Cleartext Credentials | FollowTCPStream.jpg]
**Evidence:** As shown in the screenshot above, the login sequence is entirely visible. Every keystroke sent from the kali machine to the server was captured, including the password.

## 💡 Remediation & Analysis
**The Problem:** Telnet (Port 23) does not use encryption. Anyone with access to the network path (via a compromised switch, rogue access point, or "Man-in-the-Middle" attack) can steal sensitive data.
**The Solution:**
1. Decommission Telnet: Disable the Telnet service on all production servers.
2. Implement SSH: Use SSH (Secure Shell) on port 22. SSH encrypts the entire session, making captured packets indecipherable to attackers.
3. Firewall Rules: Block Port 23 at the network perimeter to prevent external access.

## 🏁 Conclusion
This lab highlighted the difference between "functional" and "secure" networking. While Telnet worked for communication, its lack of security makes it a liability. This project strengthened my ability to use Wireshark for incident investigation and Protocol validation.
