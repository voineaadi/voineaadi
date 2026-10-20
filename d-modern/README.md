# Active Production Infrastructure & Modern Lab Directory (`d-modern/`)

## Executive Overview
The `d-modern/` directory represents the operational nucleus of the multi-OS production fleet and modern systems engineering lab environment [9, 51]. Built upon a zero-trust, high-availability architecture, this knowledge base documents active hardware-software topologies, kernel-level security rules, hypervisor resource boundaries, and cross-platform automation pipelines [1, 9, 37, 56].

To maintain absolute transparency and auditability, this repository distinguishes between **Verified Production Baselines** (backed by completed, solved technical tickets) and **Active Expansion Technologies** (architecturally specified and documented in the strategic roadmap, but currently **- In Progress -** with no solved tickets yet) [1, 14, 71].

---

## Professional Growth & Active Engineering Roadmap
> 💡 **Engineering Context & Distinction Note (Eindhoven / Brainport Alignment)**:
> This modern infrastructure suite reflects a self-engineered laboratory designed to bridge bare-metal systems administration with modern DevOps paradigms. 
> - **Verified Production Baselines (100% Solved Tickets)**: Bare-metal OS stabilization, endpoint security hardening (OpenBSD `pf`, LuLu egress, LSASS `RunAsPPL`), macOS keep-alive assertions, 24-step maintenance runbooks, and Dutch GDPR data sanitization [12, 37, 75, 87].
> - **Active Expansion & In-Progress Technologies (Roadmap / No Solved Tickets Yet)**: Advanced container orchestration (Docker Compose fabrics, `k3s` Kubernetes), Infrastructure as Code (Ansible playbooks, Terraform state), hypervisor guest provisioning (KVM `libvirt` VMs), and time-series observability (Prometheus & Grafana) are explicitly tagged as **`- In Progress -`** [6, 20, 22, 71, 74]. I am actively expanding into these domains with high enthusiasm to adopt and apply them in enterprise high-tech roles.

---

## Subdirectory Directory Architecture & Module Mapping (`d1` to `d10`)

| Subdirectory | System Module & Operational Scope | Architectural Focus & Technology Status |
| :--- | :--- | :--- |
| **`d1/` (`D.1. Home Lab`)** [51] | Multi-Node Topology & Power Architecture | • **Production Baseline (Solved)**: 2-Stage Power Lineage (ZUBR TrueRMS relay, Brennenstuhl OVP, TED Servo AVR, CyberPower UPS) [10, 52].<br>• **`- In Progress -`**: V3 Enterprise Target Grid (DIN-rail ZUBR D2, VFI Double-Conversion UPS) & Etherwake WoL Backup Engine [5, 10, 54]. |
| **`d2/` (`D.2. EP-WIN-02`)** [9] | Multi-LLM Sandbox & Workstation | • **Production Baseline (Solved)**: Dual-boot Windows 11 / Ubuntu Linux dev node, DriverStore Explorer purges, WinSxS servicing repair, and Lynis security auditing (>85 score) [2, 9, 75]. |
| **`d3/` (`D.3. EP-WIN-03`)** [9] | Mobile Remote Administration Node | • **Production Baseline (Solved)**: Mobile power state tuning (99% CPU limit on battery, G-Helper performance curves), uBlock DNS filtering, and DDU GPU driver resets [9, 28]. |
| **`d4/` (`D.4. EP-WIN-04`)** [9] | Secondary Testbed & Driver Interoperability | • **Production Baseline (Solved)**: Servicing stack recovery, HID selective suspend polling fix (cursor skipping/typing fix), and BitLocker partition encryption [5, 19, 33]. |
| **`d5/` (`D.5. EP-LIN-01`)** [9, 56] | Headless Linux KVM Hypervisor Node | • **Production Baseline (Solved)**: Headless Ubuntu 24.04 LTS server, UFW firewall, systemd service management [4, 56].<br>• **`- In Progress -`**: Native KVM/`libvirt` 300GB storage pool allocation (`AI-LEGACY-SYSINT-2026-07-08-STRG-01`) [4, 58]. |
| **`d6/` (`D.6. EP-MAC-01`)** [8, 9] | Core Systems Engineer Workstation | • **Production Baseline (Solved)**: Apple Silicon macOS 15+ Sequoia workstation, 3-Tier Security (OpenBSD `pf` kernel firewall, LuLu egress filter, Secure Enclave UID >= 501 isolation), and SIP/Continuity token deconfliction [8, 37, 41, 62]. |
| **`d7/` (`D.7. Maintenance`)** [6, 69] | Modern Maintenance & Anti-Drift Suite | • **Production Baseline (Solved)**: Modern Maintenance Protocol V1 (24-step manual checklist, DISM/SFC servicing repair) [6, 13, 69].<br>• **`- In Progress -`**: Maintenance V2 (Idempotent PowerShell `.ps1`), V3 (Python Daemon), & V4 (Ansible Orchestration) [66]. |
| **`d8/` (`D.8. Automation & Orchestration`)** [6, 17] | Cross-Platform Automation Engine | • **Production Baseline (Solved)**: PowerShell / Bash administrative scripting basics [71].<br>• **`- In Progress -`**: Python Socket Liveness Watchdogs, Ansible WinRM/OpenSSH Playbooks, Terraform IaC, Docker Compose Fabrics, & `k3s` Kubernetes Clusters [6, 17, 20, 71]. |
| **`d9/` (`D.9. Networking`)** [3, 15] | Enterprise Network Topology & Perimeter | • **Production Baseline (Solved)**: Subnet mapping, NetBIOS/SMBv1 isolation, Cloudflare/Google secure DNS, SSH tunneling baseline [3, 15, 44].<br>• **`- In Progress -`**: Enterprise DNS/DHCP Subnet Topology & Advanced Network Filtering (`SYS-MODERN-NET-2026-10-HARDENING-01`) [22]. |
| **`d10/` (`D.10. Cybersecurity`)** [16, 75] | Zero-Trust Hardening & Compliance | • **Production Baseline (Solved)**: LSASS `RunAsPPL` credential protection, Group Policy USB restrictions, Lynis auditing (>85 score), and Dutch GDPR data sanitization [16, 30, 75, 82].<br>• **`- In Progress -`**: Prometheus & Grafana Metrics Pipeline (`SYS-MODERN-OBS-2026-10-TELEMETRY-01`) [17, 23]. |

---

## Power Resilience & Compute Fleet Architecture (`d1`, `d2`, `d5`)

### 1. Multi-Stage Power Conditioning Lineage (`d1/`)
To eliminate utility grid voltage spikes, brownouts, and floating neutral risks in residential testing environments, electrical supply is filtered through a multi-tier evolutionary protection chain [10, 52]:
- **V1 Legacy Chain — Production Baseline (Solved Ticket)**: Wall Outlet $\longrightarrow$ Electrical Panel (Panasonic VIKO Sockets) $\longrightarrow$ Surge Strip $\longrightarrow$ TED 2100SVC Servo AVR $\longrightarrow$ CyberPower UPS $\longrightarrow$ Endpoints [52, 53].
- **V2 Current Romania Stack — Production Baseline (Solved Ticket)**: Countryside Utility Grid $\longrightarrow$ ZUBR R116Y TrueRMS Digital Relay (0.04s emergency cutoff) $\longrightarrow$ External Surge Protector $\longrightarrow$ Brennenstuhl Premium-Line OVP (26,000A EMI/RFI noise filter) $\longrightarrow$ TED 2100SVC Servo AVR $\longrightarrow$ CyberPower CP1500EPFCLCD Pure Sine UPS $\longrightarrow$ Lab Fleet [10, 52, 53].
- **V3 Enterprise Netherlands Grid — `- In Progress -` (Planned Expansion, No Solved Ticket Yet)**: Main Utility Grid $\longrightarrow$ DIN-Rail ZUBR D2 Voltage Relay $\longrightarrow$ Type 1/2 Surge Protection Devices (SPD) $\longrightarrow$ Thermal-Magnetic MCB $\longrightarrow$ In-Wall Copper ($2.5\,	ext{mm}^2$) $\longrightarrow$ Industrial Outlets $\longrightarrow$ Secondary ZUBR R116Y Relay $\longrightarrow$ Brennenstuhl OVP $\longrightarrow$ TED Servo AVR $\longrightarrow$ VFI Online Double-Conversion UPS (0ms transfer time) $\longrightarrow$ Fleet [10, 52, 54].

### 2. KVM Hypervisor Topology & Guest Node Boundaries (`d1/`, `d5/`)
Hosted on **`EP-LIN-01`** (Ubuntu Linux 24.04 LTS headless partition) [4, 56]:
- **Ubuntu 24.04 LTS Headless Host & UFW Firewall — Production Baseline (Solved Ticket)**: Base OS installation and network security configuration [4, 56].
- **KVM / `libvirt` 300 GB Storage Pool Boundary — `- In Progress -` (Planned Ticket: `AI-LEGACY-SYSINT-2026-07-08-STRG-01`)**: Allocation of dedicated storage pool boundary (`/var/lib/libvirt/images/homelab-pool`) [4, 5, 58].
- **`VM-SYSINT-WIN-01` (Windows Server AD/DC Eval VM) — `- In Progress -` (Planned Ticket: `AI-LEGACY-SYSINT-2026-07-08-SYSINT-03`)**: Windows Server Evaluation instance configured for Active Directory & Domain Controller simulation with `slmgr /rearm` trial tracking [4, 13, 57].
- **`VM-SYSINT-LIN-01` (Ubuntu Microservices Guest Node) — `- In Progress -` (Planned Ticket: `AI-LEGACY-SYSINT-2026-07-08-SYSINT-04`)**: Ubuntu Linux guest node for microservice isolation enforcing non-root execution [4, 5, 57].

### 3. Centralized Etherwake WoL Backup Pipeline (`d1/`, `d2/`, `d5/`)
- **Etherwake WoL Backup Engine — `- In Progress -` (Planned Ticket: `AI-LEGACY-SYSINT-2026-07-08-BKPENG-05`)**: Off-site backup automation running headlessly on `EP-LIN-01` targeting a secondary 750 GB HDD mounted on `EP-WIN-02` [5, 51, 57]:
```
[EP-LIN-01 Cron Trigger] ──(Etherwake WoL Magic Packet)──> [EP-WIN-02 Desktop Boot]
                                                                  │
[Graceful Remote SSH Shutdown] <──(Client-Side Encrypted Sync)────┘
```
1. `EP-LIN-01` issues an `etherwake` Magic Packet to wake `EP-WIN-02` [5, 57].
2. Upon network registration, client-side encrypted sync routines (`rsync` / `rclone`) transfer sanitized delta backups to the 750 GB target pool [5, 57].
3. `EP-LIN-01` issues an authenticated remote OpenSSH shutdown command (`sudo shutdown -h now`) to preserve power [5, 57, 58].

---

## Secure Enclave & Workstation Security Architecture (`d3/`, `d4/`, `d6/`)

### 1. macOS ARM64 3-Tier Security Stack (`d6/`) — Production Baseline (Solved Tickets)
The primary workstation (`EP-MAC-01`, Apple Silicon M-Series, macOS 15+ Sequoia) enforces a multi-layered security boundary combining kernel network filtering, application egress controls, and biometric hardware isolation [8, 9, 37, 41]:

```
┌────────────────────────────────────────────────────────────────────────┐
│  Layer 7 Outbound Application Firewall: LuLu                           │
│  - Prompts for unapproved 3rd-party egress sockets                     │
│  - Automatically passes Apple-signed daemons (sharingd, rapportd)       │
├────────────────────────────────────────────────────────────────────────┤
│  Layer 3/4 Inbound Kernel Firewall: OpenBSD Packet Filter (pf)          │
│  - Configured via /etc/pf.anchors/custom.security                      │
│  - Permits stateful outbound TCP/UDP/ICMP & local LAN mDNS (UDP 5353)   │
│  - Blocks unsolicited inbound probes; enables ICMP ping drop stealth   │
├────────────────────────────────────────────────────────────────────────┤
│  Hardware Security Enclave & Multi-Profile Isolation                   │
│  - Enforces Touch ID biometric isolation across UIDs                   │
│  - Restricts duplicate fingerprints between Admin & Standard (UID >=501)│
└────────────────────────────────────────────────────────────────────────┘
```

- **OpenBSD Packet Filter (`pf`) Kernel Rules — Production Baseline (Solved Ticket)**: Native kernel firewall rules loaded via `/etc/pf.conf` and custom anchors with ICMP stealth toggling [37, 39].
- **LuLu Outbound Egress Filter — Production Baseline (Solved Ticket)**: Layer 7 process monitor set to "Allow Apple Signed Programs" [40, 41].
- **Identity Services (`IDS`) Deconfliction — Production Baseline (Solved Ticket)**: Continuity cellular token purges and daemon restarts (`sudo killall -9 identityservicesd avconferenced`) [12, 60, 64].

### 2. Mobile Windows & Multi-OS Hardening (`d3/`, `d4/`, `d2/`) — Production Baseline (Solved Tickets)
- **`EP-WIN-03` Mobile Admin Tuning — Production Baseline (Solved Ticket)**: Power state frequency limits (99% CPU limit on battery), G-Helper performance curves, uBlock Origin DNS filtering, and DDU GPU resets [9, 12, 28].
- **`EP-WIN-04` Driver Interoperability Remediation — Production Baseline (Solved Ticket)**: Disabled selective suspend across HID power management nodes to eliminate cursor skipping and restore 100% typing accuracy [19, 46]. Enforces BitLocker encryption across system partitions [12, 19, 33].

---

## Modern Maintenance, Automation & Networking (`d7/`, `d8/`, `d9/`, `d10/`)

### 1. Modern Maintenance Protocol Progression (`d7/`)
- **Maintenance V1 Manual Baseline — Production Baseline (Solved Ticket: `SYS-LEGACY-SYSINT-2026-07-12-MODERNMAINT-09`)**: Deterministic 24-step maintenance runbook covering `sfc /scannow`, `DISM /RestoreHealth`, `SoftwareDistribution` cache resets, and `netsh winsock reset` [6, 13, 50, 69].
- **Maintenance V2 Scripted (PowerShell `.ps1`) — `- In Progress -` (Planned Ticket: `SYS-MODERN-MAINT-2026-10-PS2-01`)**: Idempotent PowerShell anti-drift enforcement scripts executed silently via Task Scheduler [7, 66].
- **Maintenance V3 Automated Daemon — `- In Progress -` (Planned Roadmap)**: Cross-platform Python background daemon monitoring PID drift and storage usage [66].
- **Maintenance V4 Orchestrated — `- In Progress -` (Planned Roadmap)**: Ansible playbooks orchestrated from Linux control plane over WinRM/OpenSSH with AIOps telemetry triggers [66].

### 2. Scripting, Automation, IaC & Container Pipelines (`d8/`)
- **PowerShell & Bash Scripting Basics — Production Baseline (Solved Ticket)**: Administrative system scripts and environment configuration utilities [71].
- **Python Liveness Watchdogs — `- In Progress -` (Planned Expansion, No Solved Ticket Yet)**: Python scripts monitoring Docker socket APIs and process liveness inside virtual environments (`venv`) [17, 71, 79].
- **Ansible WinRM & OpenSSH Playbooks — `- In Progress -` (Planned Ticket: `SYS-MODERN-IAC-2026-10-ANSIBLE-01`)**: Cross-platform Ansible configuration management playbooks for zero-touch state enforcement across `EP-WIN-02` and `EP-LIN-01` [6, 20, 22].
- **Terraform Declarative IaC — `- In Progress -` (Planned Ticket: `SYS-MODERN-IAC-2026-10-TERRAFORM-01`)**: Declarative state configuration and cloud stack deployment scripts [7, 23, 71].
- **Docker Compose Multi-Tier Service Fabrics — `- In Progress -` (Planned Ticket: `SYS-MODERN-SYSINT-2026-10-HOMELAB-02`)**: Multi-container Docker Compose fabrics for microservices and monitoring dashboards [6, 16, 21].
- **Lightweight `k3s` Kubernetes Cluster Initialization — `- In Progress -` (Planned Ticket: `SYS-MODERN-SYSINT-2026-10-K3S-03`)**: Lightweight Kubernetes cluster architecture with health checks and Helm charts [6, 16, 21].

### 3. Enterprise Perimeter, Zero-Trust & Observability (`d9/`, `d10/`)
- **Network Perimeter Isolation (`d9/`) — Production Baseline (Solved Ticket)**: Subnet topology enforcing NetBIOS disablement, SMBv1 termination, Cloudflare/Google DNS, and SSH tunneling baseline [3, 15, 44].
- **Enterprise DNS/DHCP Subnet Topology — `- In Progress -` (Planned Ticket: `SYS-MODERN-NET-2026-10-HARDENING-01`)**: Advanced network filtering and UFW boundary enforcement [4, 22].
- **Credential Protection & Access Control (`d10/`) — Production Baseline (Solved Ticket)**: LSASS `RunAsPPL` protected process light, Group Policy USB restrictions (`gpedit.msc`), Lynis audit score >85, and Dutch GDPR PII data scrubbing [8, 16, 30, 75, 82].
- **Prometheus & Grafana Multi-Node Metrics Pipeline — `- In Progress -` (Planned Ticket: `SYS-MODERN-OBS-2026-10-TELEMETRY-01`)**: Time-series metric collection, multi-node Grafana dashboards, and Netdata thermal profiling [8, 17, 23].
- **Advocatus Diaboli & Multi-LLM Agentic API Orchestration — `- In Progress -` (Planned Tickets: `AI-MODERN-AIOPS-2026-10-PROMPT-02` & `ORCHESTRATION-01`)**: Transitioning manual 4-tier prompt chaining to programmatic Google AI Studio and Cursor agentic workflows [8, 18, 24].
