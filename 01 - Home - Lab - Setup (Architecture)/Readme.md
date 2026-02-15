# Project 1: Isolated Virtual Security Laboratory

## Objective:
    To desing and deploy a secure sandboxed virtualization environment for executing offensive secuirty tools and defensive monitoring without risking the integrity of the host machine or the home network.

## Architecture and Topology:
- **Hypervisor:** Oracle VirtualBox 7.2.4_Debianr170995
- **Network Mode:** NAT Network (Isolated)
- **Subnet:** 10.0.2.0/24
- **Nodes:**
    - **Attacker:** Kali Linux (Rolling Edition)
    - **Victim:** Metasploitable 2 (Linux-based vulnerable server)

## Configuration Steps:
1. **Network Segmentation:** Created a dedicatied 'Nat Network' in VirtualBox.  This ensures that while VMs can talk to each other, they cannot communicate with other devices on my physical home Wi-Fi.
2. **Resource Allocation:** - Kali Linux: 4GB RAM, 2 CPUs (Optimized for performance.
                            - Metasploitable: 512MB RAM, 1 CPU (Low-resource legacy server).
3. **Hardening:** Disabled shared dclipboard and drag-and-drop between the host and the guest VMs to prevent "VM Escape" risks.


##Verification (Proof of Work)
- **VLAN/Subnet Logic:** Learned how to define custom IP ranges and gateway addresses.
- **Risk Management:** Understood the importance of isolation when handling potentially malicious tools or vulnerable software.
