# [Project Name: Social Engineering]

## 📝 Executive Summary
**Objective:** To demonstrate the effectiveness of credential-harveesting attacks and the necessity of Multi-Factor Authentication (MFA).
**Outcome:** Successfully cloned a legitimate login portal using the Social-Egineer Toolkit (SET) and captured plaintext credentials from a victim node in a controlled environment.

## 🛠️ Environment & Tools
* **Attacker:** Kali Linux (SET - Social-Engineer Toolkit)
* **Target:** Ubuntu 22.04 (Web Browser)
* **Protocol:** HTTP (Port 80)
* **Network:** Isolated VirtualBox NAT Network

## 🛡️ Step-by-Step Methodology
1. **Toolkit Initialization:** Launched setoolkit and selected teh Website Attack vector for Credential Harvesting.
2. **Site Cloning:** Configured the toolkit to clone a standard login interface, hosting the malicious replica on the attacker's local IP.
3. **Victim Interaction:** Navigated tot he attacker's IP from the victim machine, simulating a user clicking a link in a phishing email.
4. **Data Exfiltration:** Monitored the SET listener to capture POST requests containing the victim's submitted credentials.

## 📊 Findings & Evidence
 - **Vulnerability:** Lack of user awareness regarding URL verification and the use of unencrypted (HTTP) login forms.
 - **Evidence:** The attacker terminal successfully logged the following plaintext data:
   - Username: victim_account@example.com
   - Password: Spring2026!

## 💡 Remediation & Analysis
**The Problem:** Technical controls (firewalls/antivirus) are often bypassed by social engineering. If a user is tricked into giving away their password, the strongest encryption in the world cannot protect the account.
**The Solution:** 
1. **FIDO2/WebAuthn:** Move beyond SMS-based MFA to hardware security keys (like Yubikeys) which are resistant to phishing.
2. **Email FIltering:** Implement DMARC, DKIM, and SPF records to reduce the ikelyhood of spoofed emamils reaching users.
3. **User Training:** Conduct regular "Phishing Simulations" to train employees on how to inspect URLs and certificates before entering data.

## 🏁 Conclusion
This lab highlights that security is a combination of People, Process, and Technology. By simulating the attacker's perspective, I have gained a better understanding of how to defend against one of the most common entry points for ransomware and data breaches.
