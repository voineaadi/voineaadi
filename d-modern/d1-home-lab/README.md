# Home Lab Master Architecture & Ecosystem Specification

Unified Technical Baseline: A→Z Power Resilience, Multi-OS Fleet Topology, and KVM Migration Blueprint
Master Baseline Metadata:
 • Document Identifier: MODERN-SPEC-2026-10-28-HOMELAB-MASTER.V4
 • Megaticket ID: AI-MODERN-SYSINT-2026-10-28-HOMELAB-01.V2.NotebookLM.Lin.Manual
 • Target Repository: homelab-core / Issue #1
 • Operational Pipeline: [CURRENT PHYSICAL STATE] ──> [MIGRATION WORKFLOW/RUNBOOK] ──> [FUTURE AUTOMATED STATE]

1. Layer 1: A→Z Power Resilience Architecture
1.1 Executive Summary & Evolutionary Comparison Matrix
The Power Resilience Architecture resolves electrical grid instability, floating neutral hazards, and high-voltage transient spikes. It establishes a multi-stage conditioning chain ensuring 100% uptime, zero hardware degradation, and zero component conflict across three distinct evolutionary phases:

• V1 — Legacy Baseline (Inherited Setup): A preliminary setup featuring a Re-Worked Modern Electrical Panel with Panasonic VIKO Sockets, feeding an External Surge Protector, a TED 2100SVC Servomotor Stabilizer, and an aging Line-Interactive CyberPower UPS. While offering basic spike absorption, it lacks active microsecond voltage relay protection against severe floating neutrals.
• V2 — Current Stack (Romania Temporary Residence): A highly effective single-phase protection stack tailored for unstable countryside grids without main panel modification. Electricity flows from the wall outlet through a ZUBR R116Y TrueRMS digital relay (0.04s emergency cutoff), an External Surge Protector, a Brennenstuhl Premium-Line OVP (26,000A EMI/RFI noise suppression), a TED 2100SVC Servo AVR, a CyberPower CP1500EPFCLCD Pure Sine Wave UPS, and a Passive Resilience Layer (20–700W load profile).
• V3 — Enterprise Target (Netherlands Permanent Residence): Represents the full datacenter-grade infrastructure upgrade. The physical and electrical lineage originates from the stable utility grid and feeds directly into a main distribution wall panel featuring a DIN-Rail ZUBR D2 digital voltage relay (providing whole-house millisecond disconnects), followed by Type 1/2 Surge Protection Devices (SPD) for lightning/inductive transient absorption, and Wall Panel Thermal-Magnetic Breakers for primary circuit overcurrent/short-circuit protection. Power is routed through dedicated in-wall 2.5mm² copper wiring to high-grade industrial outlets (Panasonic / VIKO), leading to a secondary point-of-use ZUBR R116Y local relay, external surge protector, Brennenstuhl Premium-Line OVP (26,000A EMI/RFI noise suppression), TED 2100SVC servomotor AVR, and a VFI Online Double-Conversion Uninterruptible Power Supply (0ms transfer time), ensuring 100% continuous power integrity for the Enterprise Home Lab.

Feature / Metric | V1 — Legacy Baseline | V2 — Romania Stack | V3 — Netherlands Target
--- | --- | --- | ---
Grid Environment | Unstable Grid | Unstable Countryside Grid (No Panel Mods) | Stable Dutch Grid + Whole-House Main Panel Upgrades
Primary Panel Cutoff & Relay | Upgraded Panel / VIKO Sockets (No Voltage Relay) | ZUBR R116Y (TrueRMS 0.04s Cutoff at Outlet) | DIN-Rail ZUBR D2 (Main Panel) + ZUBR R116Y (Point-of-Use)
Surge / Transient Protection | External Surge Strip | External Surge Strip + Brennenstuhl OVP (26,000A) | Type 1/2 SPD (Main Panel) + External Surge Strip + Brennenstuhl OVP
Panel Overcurrent Protection | Standard Residential Breakers | Standard Residential Breakers | Wall Panel Thermal-Magnetic Breakers (Main Panel Protection)
Wiring & Outlets | Standard Residential Wiring | Standard Outlet with Plug-In Relays | In-Wall 2.5mm² Copper + Industrial Outlets (Panasonic / VIKO)
Voltage Regulation | TED 2100SVC Servo AVR | TED 2100SVC Servo AVR (Pure Sine Wave) | TED 2100SVC Servo AVR
UPS Topology & Transfer Time | Line-Interactive (Degraded Battery, 4–10ms) | CyberPower CP1500EPFCLCD (4–8ms Transfer) | VFI Online Double-Conversion UPS (0ms Transfer Time)
Load Profile & Headroom | Unmanaged Load | Passive 20–700W (Low Thermal Stress) | Passive 20–700W on 1500–2700W UPS (7–25% Utilization)

1.2 Technical Validation & Electrical Engineering Principles
A. Zero Component Conflict ("MOV-on-MOV" Safety Proof):
 A critical engineering validation of the V2 and V3 power chains is the elimination of dangerous MOV series conflicts. The ZUBR R116Y and ZUBR D2 relays operate strictly as digital voltage monitoring relays utilizing TrueRMS microprocessors to trigger a millisecond hard disconnect; they contain no Metal Oxide Varistors (MOVs). The Brennenstuhl Premium-Line OVP acts as an industrial noise/OVP filter providing 3-way protection with 26,000A clamping capacity. The Wall Panel Thermal-Magnetic Breakers provide bimetallic and electromagnetic arc suppression without MOV overlap. Consequently, each stage operates in a distinct functional domain, avoiding cascading varistor thermal runaway.
B. V3 Enterprise Online Double-Conversion UPS Selection:
 For the permanent V3 Netherlands deployment, two professional online double-conversion (VFI) UPS options are validated:
 • Option A: PowerWalker VFI 1500 ICT IoT — True Online Double-Conversion (0ms transfer) with integrated IoT/network telemetry card for real-time monitoring via Prometheus/Grafana.
 • Option B: TED Electric Rackmount 3000VA / 2700W (2U) — True Online Double-Conversion providing massive power headroom. Running a 20–700W home lab load results in a 7–25% utilization rate, maximizing battery lifespan and heat dissipation.

1.3 Sequential Protection Chains (V1 ──> V2 ──> V3)
🔴 V1 Legacy Chain:
 [Unstable Grid] ──> [Re-Worked Modern Electrical Panel + Panasonic VIKO Sockets] ──> [External Surge Protector] ──> [TED 2100SVC Servo AVR] ──> [CyberPower UPS] ──> [End-Devices]
🟡 V2 Romania Chain:
 [Unstable Countryside Grid] ──> [ZUBR R116Y Relay (0.04s Cutoff)] ──> [External Surge Protector] ──> [Brennenstuhl OVP (26,000A)] ──> [TED 2100SVC Servo AVR] ──> [CyberPower UPS] ──> [Passive Resilience Layer (20–700W)] ──> [Protected Lab Endpoints]
🟢 V3 Netherlands Enterprise Chain:
 [Utility Grid] ──> [DIN-Rail ZUBR D2] ──> [Type 1/2 SPD] ──> [Wall Panel Thermal-Magnetic Breakers] ──> [In-Wall Copper (2.5mm²)] ──> [Industrial Outlets] ──> [ZUBR R116Y Local Relay] ──> [External Surge Protector] ──> [Brennenstuhl OVP] ──> [TED 2100SVC Servo AVR] ──> [VFI Online UPS] ──> [Enterprise Home Lab]

1.4 Visual Schematic: Power Resilience & Conditioning Lineage

![Power Resilience & Conditioning Lineage](./assets/Power%20Resilience%20&%20Conditioning%20Lineage.png)

1. Layer 2–9: Compute Fleet Topology & KVM / Native Containerization Blueprint
2.1 Fleet Hardware & Endpoint Topology Matrix
Endpoint ID | Platform & Architecture | Operating System | Environment & Role Profile
--- | --- | --- | ---
EP-WIN-01 | x86_64 (Intel) | Windows 11 Pro | Enterprise Hardened Profile 1 / Workstation
EP-WIN-02 | x86_64 (Intel) | Windows 11 Home | Desktop 2 / Target for WoL Encrypted Backups (750 GB HDD)
EP-WIN-03 | x86_64 (Intel) | Windows 11 Pro | Laptop 1 / Mobile Profile 1
EP-WIN-04 | x86_64 (AMD) | Windows 11 Home | Laptop 2 (Windows Partition) / Mobile Profile 2
EP-LIN-01 | x86_64 (AMD) | Ubuntu Linux 24.04 LTS | Laptop 2 (Linux Partition) / Host KVM & Native Container Runtime (Docker & K3s)
EP-MAC-01 | ARM64 (Apple M-Series) | macOS 15+ | Laptop 3 / Mobile Profile 4 (Dual-Profile: Admin & Standard)

2.2 Architecture & Virtualization Allocation
Laptop 2 operates as a dual-boot system containing EP-WIN-04 and EP-LIN-01. A dedicated 300 GB storage pool boundary is allocated on Laptop 2 for KVM virtual machines and container workloads. Under Ubuntu Linux (EP-LIN-01):

 1. Native Containerization: Docker & K3s micro-services run directly on host OS (EP-LIN-01) for zero overhead and maximum performance.
 2. VM-SYSINT-WIN-01: Isolated KVM Guest VM running Windows Server Evaluation for Active Directory & Domain Controller simulation. Maintains a strict tracking log for trial resets (slmgr /rearm).

2.3 Centralized WoL & Encrypted Backup Pipeline
Automated backup operations are driven by EP-LIN-01 targeting the dedicated 750 GB HDD mounted on EP-WIN-02 (Desktop 2). The automated sequence executes via an etherwake Magic Packet over the Tailscale Mesh Network, performs client-side encrypted syncs via rsync/rclone, and terminates with a graceful remote SSH shutdown command.

2.4 Visual Schematic: Master Home Lab Topology

![Master Home Lab Topology](./assets/Master%20Home%20Lab%20Topology.png)

1. Active Execution Queue & Migration Task Tickets
Master Megaticket ID: AI-MODERN-SYSINT-2026-10-28-HOMELAB-01.V2.NotebookLM.Lin.Manual
 Target Repository: homelab-core / Issue #1

 The migration workflow/runbook executes across 6 standardized task tickets:
• Task 1: Allocate Sandbox Resource Boundary
   Ticket ID: 1.AI-MODERN-SYSINT-2026-10-28-STRG-01.V2.Local.Sandbox.Lin.Manual
   Technical Scope: Reserve 300 GB on Laptop 2 drive for VM disk pool and container storage. Prepare bootable USB fallback drive for partition protection.
• Task 2: Initialize Hypervisor Core & Native Container Runtime
   Ticket ID: 2.AI-MODERN-SYSINT-2026-10-28-HYPER-02.V2.Local.Sandbox.Lin.Manual
   Technical Scope: Provision KVM (qemu-kvm, libvirt, virt-manager) and native Docker/K3s runtime environment on Ubuntu Linux host (EP-LIN-01).
• Task 3: Provision Windows Server Evaluation Node
   Ticket ID: 3.AI-MODERN-SYSINT-2026-10-28-SYSINT-03.V2.Local.Sandbox.Win.Manual
   Technical Scope: Deploy VM-SYSINT-WIN-01 inside KVM. Maintain slmgr /rearm tracking log extending trial clock up to 6 cycles.
• Task 4: Deploy Cybersecurity Hardening Baseline Policy (Per-Device)
   Ticket ID: 4.AI-MODERN-SYSINT-2026-10-28-CYBER-04.V2.Local.Sandbox.Multi.Manual
   Technical Scope: Manually apply cybersecurity baseline hardening on each physical endpoint and VM before network integration (Zero Trust per-device policy).
• Task 5: Deploy Secure Mesh Networking via Tailscale Integration
   Ticket ID: 5.AI-MODERN-SYSINT-2026-10-28-MESH-05.V2.Local.Sandbox.Multi.Manual
   Technical Scope: Install and authenticate Tailscale client on each hardened device. Configure Tailnet, MagicDNS, and ACLs for encrypted peer-to-peer interconnectivity.
• Task 6: Infrastructure Automation & Configuration Management via Ansible
   Ticket ID: 6.AI-MODERN-SYSINT-2026-10-28-ANSIBLE-06.V2.Local.Sandbox.Lin.Manual
   Technical Scope: Deploy Ansible on EP-LIN-01. Configure inventory over Tailscale 100.x.x.x IPs and execute Day-2 configuration management playbooks.

1. Linux Host Configuration & Automation Runbook (EP-LIN-01)
Execute the following configuration sequence on EP-LIN-01 to initialize hypervisor virtualization, storage pools, security baselines, and backup triggers:
1. KVM & Container Runtime Initialization:
    Install packages: qemu-kvm, libvirt-daemon-system, libvirt-clients, bridge-utils, virt-manager, ovmf, cpu-checker, ufw, fail2ban, rsync, etherwake, rclone, docker.io, tailscale.
    Verify virtualization support via kvm-ok and append operational user to libvirt, kvm, and docker security groups.

1. Storage Pool Provisioning:
    Directory: /var/lib/libvirt/images/homelab-pool (300GB allocation boundary).
    Define, autostart, and initialize pool using virsh pool-define-as and virsh pool-start.

1. Network Firewall Baseline:
    Default deny incoming policy, allow outgoing, allow virbr0 bridge traffic, allow tailscale0 interface, and enable UFW.

1. Automated WoL Backup Script Workflow:
    Trigger Wake-on-LAN magic packet to Desktop 2 (EP-WIN-02 MAC address).
    Wait for endpoint boot, mount encrypted backup target over Tailscale IP, execute rsync/rclone synchronization, and issue graceful remote power off via SSH.
