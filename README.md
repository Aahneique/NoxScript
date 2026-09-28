# NoxScript

**The Permanent Airgap Utility for Extreme System Isolation**

NoxScript is a purposely destructive security tool built to permanently and irreversibly cut a Linux machine off from the outside world. If you need absolute cryptographic and physical isolation, NoxScript transforms a standard daily-driver OS into an impenetrable, offline secure enclave.

## Philosophy

Just turning off Wi-Fi or yanking the Ethernet cable isn't enough when you're dealing with high-stakes security. Background services wake up, malware tries to side-load network drivers, and automated updates can accidentally restore your connection.

NoxScript operates on a strict zero-trust basis. It doesn't just toggle your connection off—it systematically dismantles the operating system's ability to communicate with network hardware at the daemon, interface, kernel, and firewall levels.

## Installation

NoxScript is designed as a standalone, single-file utility. You can pull it directly from this repository, place it in your local binaries, and make it executable in one command:

```bash
sudo curl -sSL [https://raw.githubusercontent.com/Aahneique/NoxScript/main/noxscript.py](https://raw.githubusercontent.com/Aahneique/NoxScript/main/noxscript.py) -o /usr/local/bin/noxscript && sudo chmod +x /usr/local/bin/noxscript
```

Once installed, you can run sudo noxscript from anywhere in your terminal.

## Core Capabilities

NoxScript executes a rigorous, four-tier lockdown protocol:

1. **Daemon Neutralization:** It hunts down and disables all network-managing background services. We mask these services at the system level, meaning even automated update managers cannot accidentally revive them in the background.
2. **Hardware Severing:** ssues hard blocks to all wireless and Bluetooth radios, and forcefully brings down all physical network interfaces (keeping only the internal loopback alive so local apps don't crash).
3. **Kernel Module Blacklisting:** Injects strict configurations to blacklist networking hardware drivers straight at the kernel level. Even if a rogue payload attempts to manually mount a Wi-Fi or Ethernet driver, the OS will forcefully reject it.
4. **Persistent Drop-All Firewall:** Establishes an absolute, default-drop firewall policy. It injects a custom boot-level service that ensures all inbound, outbound, and forwarded traffic is dropped before the system even finishes booting up.

## Primary Use Cases

* **Offline Root Certificate Authorities:** Set up an airgapped machine for managing your PKI, generating root certificates, and securely signing intermediate authorities.
* **Malware Detonation & Analysis:** Ensure that highly infectious or self-propagating malware variants physically cannot phone home, spread to your local network, or leak data during forensic analysis.
* **Cryptocurrency Cold Storage:** Build an ultra-secure, completely offline environment for generating cryptographic keys and signing transactions without the lingering fear of remote exfiltration.
* **Journalistic & Whistleblower Workstations:** Secure highly sensitive documents, communications drafts, and raw evidence on a machine that cannot be compromised by remote surveillance or spyware.
* **Secure Data Archival:** Maintain sensitive intellectual property or personal archives on a machine permanently shielded from the internet.

## How to Use NoxScript

Because of how deeply this modifies your system, there is no silent or accidental execution.
You must run the tool with sudo noxscript. Upon launch, you'll be greeted with a brutalist warning detailing exactly what is about to happen. The system will halt and wait for you to manually type a specific confirmation keyword.
Once confirmed, you can sit back. The execution is entirely automated. You'll get a real-time terminal readout as daemons are crushed, radios are blocked, the kernel is restricted, and the firewall is sealed. A final reboot locks the permanent airgap into place.

***

**⚠️ CRITICAL WARNING ⚠️** 
NoxScript is a destructive utility. It is not a toggle switch. Do not run this on a personal daily-driver, a cloud server, or any machine that you ever intend to connect to the internet again. Reversing the effects of NoxScript requires advanced manual sysadmin intervention or a complete operating system reinstall. Use at your own absolute risk.
