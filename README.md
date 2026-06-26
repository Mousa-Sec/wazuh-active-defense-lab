# wazuh-active-defense-lab
Automated SIEM telemetry, real-time file integrity monitoring, and active response firewall drops using Wazuh

# Open-Source SIEM & Active Response Engineering Lab (Wazuh)

An end-to-end Purple Team deployment demonstrating centralized log aggregation, real-time File Integrity Monitoring (FIM), and automated Active Response threat mitigation using an open-source SIEM (Wazuh) ecosystem.

## 🏗️ Architecture Overview
The environment consists of a decentralized architecture hosted on Oracle VirtualBox:
* **Wazuh Manager Server:** Distributed on Ubuntu Server, serving as the central log correlation engine, decoder repository, and active-response conductor.
* **Linux Target Endpoint (linux-target):** Monitored Ubuntu node running the Wazuh Agent with active telemetry forwarding hooks into kernel space.

---

## 🛠️ Project Phases & Implementation Details

### Phase 1: Security Configuration Assessment (SCA Compliance)
* Configured automated system hardening audits against Center for Internet Security (CIS) benchmarks.
* Analyzed target configuration vulnerabilities, tracking critical flaws like unnecessary open ports and missing OS patches.

### Phase 2: Real-Time File Integrity Monitoring (FIM) with Content Diffs
* Transitioned the FIM subsystem (`syscheck`) from passive interval scheduling to **active real-time kernel monitoring** utilizing Linux `inotify`.
* Modified system XML definitions to enable `report_changes="yes"`, forcing the agent to securely cache text changes and ship line-by-line file modifications (`syscheck.diff`) to the central console during simulated file tampering incidents.

### Phase 3: Automated Active Response (Brute-Force Mitigation)
* Engineered a live digital tripwire directly in the server registry (`ossec.conf`).
* Developed a dynamic, tiered defense system utilizing severity threshold levels to monitor system telemetry waterfalls (PAM, local `su` authentication, and `unix_chkpwd`).
* Configured the system to invoke local script execution (`firewall-drop`), dynamically blocking adversarial IP addresses via system firewalls (`iptables`) for 180 seconds when brute-force thresholds are breached.

---

## 📊 Proof of Concept & Forensic Artifacts
*(Tip: Drop the screenshots you took during our lab right here to show your work!)*

* **Real-Time FIM Alert Triggered:** `[Insert image_221feb.png here]`
* **Forensic File Content Diff Collected:** `[Insert image_228ca4.png here]`
* **Active Response Firewall Block Fired:** `[Insert image_bc29ca.png here]`

---

## 🚀 Key Takeaways & Skills Demonstrated
* **SIEM Tuning & Log Analysis:** Deep understanding of system log waterfalls (PAM frameworks, SSHD decoders, custom rule matching).
* **XML Infrastructure-as-Code:** Configuring enterprise-grade security policies while maintaining strict syntax formatting constraints.
* **Purple Teaming Operations:** Combining defensive engineering (Blue) with automated countermeasures to dynamically neutralize adversary attack scripts (Red).
