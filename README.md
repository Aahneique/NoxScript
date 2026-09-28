# NoxScript

**The Permanent Airgap Utility for Extreme System Isolation**

NoxScript is a specialized, destructive-by-design security tool engineered to permanently and irreversibly sever a Linux machine from all internal and external networks. Built for users who require absolute cryptographic and physical isolation, NoxScript transforms a standard operating system into an impenetrable secure enclave.

## Philosophy

In high-security environments, simply turning off Wi-Fi or unplugging an Ethernet cable is insufficient. Background services can restart, malicious payloads can attempt to load network drivers, and automated updates can reset configurations. 

NoxScript operates on a zero-trust, defense-in-depth philosophy. It does not just turn off your connection; it systematically dismantles the operating system's ability to communicate with network hardware at the daemon, interface, kernel, and firewall levels.

## Core Capabilities

NoxScript executes a rigorous, four-tier lockdown protocol:

1. **Daemon Neutralization:** Systematically hunts down and disables all network-managing background services. It masks these services at the system level, meaning even automated update managers cannot accidentally revive them in the background.
2. **Hardware Severing:** Issues hard blocks to all wireless and Bluetooth radios, and forcefully brings down all physical network interfaces except the internal loopback.
3. **Kernel Module Blacklisting:** Injects strict configurations to blacklist networking hardware drivers directly at the kernel level. Even if a rogue application attempts to manually mount a Wi-Fi or Ethernet driver, the operating system will forcefully reject it.
4. **Persistent Drop-All Firewall:** Establishes an absolute, default-drop firewall policy. It injects a custom boot-level service that ensures all inbound, outbound, and forwarded traffic is dropped before the system even finishes booting up.

## Primary Use Cases

* **Cryptocurrency Cold Storage:** Create an ultra-secure, completely offline environment for generating cryptographic keys, signing transactions, and storing high-value digital assets without fear of remote exfiltration.
* **Offline Root Certificate Authorities:** Establish a secure, airgapped machine for managing Public Key Infrastructure (PKI), generating root certificates, and securely signing intermediate authorities.
* **Malware Detonation & Analysis:** Ensure that highly infectious or self-propagating malware variants cannot phone home, spread to local networks, or leak data during forensic analysis.
* **Journalistic & Whistleblower Workstations:** Secure highly sensitive documents, communications drafts, and raw evidence on a machine that physically cannot be compromised by remote surveillance or spyware.
* **Secure Data Archival:** Maintain sensitive intellectual property, legal documents, or personal archives on a machine permanently shielded from the internet.

## How to Use NoxScript

Because of the severe and permanent nature of this utility, there is no silent or accidental execution. 

To use NoxScript, the administrator must execute the tool with elevated system privileges. Upon launch, the user is presented with a clear, brutalist warning detailing the destructive nature of the sequence. The system will halt and wait for the user to manually type a specific confirmation keyword. 

Once confirmed, the execution is entirely automated. The user will see a real-time readout as daemons are crushed, radios are blocked, the kernel is restricted, and the firewall is sealed. Upon completion, a system reboot finalizes the permanent airgap.

***

**⚠️ CRITICAL WARNING ⚠️** 
NoxScript is a **destructive** utility. It is not a toggle switch. Do not run this on a personal daily-driver, a cloud server, or any machine that you ever intend to connect to the internet again. Reversing the effects of NoxScript requires advanced manual sysadmin intervention or a complete operating system reinstall. Use at your own absolute risk.
