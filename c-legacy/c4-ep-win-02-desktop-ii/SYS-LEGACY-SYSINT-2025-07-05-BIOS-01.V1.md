🎫Desktop II — UEFI BIOS Firmware Update and Platform Optimization
[ Task / Ticket ]
 • Ticket ID: SYS-LEGACY-SYSINT-2025-07-05-BIOS-01.V1.Manual.Win.Manual
 • Title: Desktop II — UEFI BIOS Firmware Update and Platform Optimization
 • Classification: Firmware Lifecycle Management / Preventive Platform Hardening
 • Target Endpoint Mapping: EP-WIN-02 (x86_64 Intel, Windows 11 Home, Standard Desktop Profile — Custom Desktop II Workstation)
 • Execution Date: 05 July 2025
[ Status: 🟢 Standby / 🟡 In Progress / 🔴 Optimize ]
 • Status: 🟢 Completed / Closed – Hardened & Stable
 • Objective: Execute a controlled UEFI BIOS firmware update on Desktop II following the 20-Year Firmware Protocol to enhance platform reliability, improve PCIe device interoperability, and strengthen firmware-level security.
 • Definition of Done: Successful manual USB flash via motherboard native UEFI utility, safe restoration of custom CPU/memory/PCIe settings (XMP, Secure Boot, TPM 2.0, Resizable BAR), and multi-reboot POST validation.
 • Constraints: Must use native UEFI BIOS flashing utility (zero OS-level flashing); FAT32 dedicated USB drive; pre-flash reset to factory defaults; power backed by AVR/UPS protection.
 • Risks / Dependencies: Power interruption during flash causing motherboard bricking; corrupted BIOS download payload; video routing reset requiring display redundancy.
 • Current Next Step: Retain current stable BIOS revision until vendor releases critical security microcode patches.
 • Evidence / Commands: Pre-flash baseline verification log; UEFI flash completion screen; post-flash POST and Secure Boot status checks.
 • Result: BIOS successfully updated to latest stable revision, PCIe acceleration enabled, XMP profile restored, 100% POST and OS stability verified.
 • Archive Location: OneNote / 14.3.Legacy.Desktop2.pdf / SYS-DEV-2025-07-DESKTOPII

Executive Summary / Complete Context
A controlled UEFI BIOS update was performed on Desktop II as part of preventive firmware lifecycle management and alignment with platform optimization protocols. The update was executed manually using a USB-based flash through the motherboard’s native firmware utility to ensure procedural control and mitigate OS-level flashing risks. System stability was verified prior to the update. Objectives achieved included enhanced firmware integrity, improved hardware compatibility, enablement of PCIe acceleration features (Resizable BAR / Above 4G Decoding), and confirmed long-term system stability under peak processing workloads.

Detailed Step-by-Step Technical Content

1. Environment & Baseline Setup
 • Device: Desktop II
 • Motherboard: Generic high-performance desktop motherboard
 • CPU: High-end multi-core processor
 • Firmware: Generic UEFI BIOS
 • Memory: DDR4 — Optimized XMP profile enabled
 • Storage: Multiple NVMe/SATA SSDs (GPT / UEFI mode)
 • GPU Outputs: HDMI + DisplayPort connected during update (display redundancy)
 • OS: Windows 11 Pro x64 (UEFI mode, Secure Boot capable)
 • Usage Profile: High-performance workstation, development, gaming
 • Location: Romania
2. Business Impact & Risk Mitigation
 • Benefits Achieved: Maintained firmware lifecycle integrity, reduced firmware vulnerability exposure, ensured compatibility with modern OS driver stacks, and preserved peak CPU/memory boost envelopes.
 • Risks Avoided: Eliminated BIOS corruption, boot failures, and recovery downtime through strict adherence to pre-flash validation protocols.
3. Step-by-Step Resolution Methodology
 • Phase 1 — Firmware Source & Authenticity Validation:
  ○ Downloaded official BIOS binary directly from manufacturer support portal.
  ○ Verified exact motherboard PCB revision and validated download file checksum authenticity.
 • Phase 2 — Dedicated USB Flash Drive Preparation:
  ○ Formatted a dedicated USB flash drive to FAT32 filesystem.
  ○ Extracted the verified BIOS binary exclusively onto the root directory of the USB drive.
 • Phase 3 — Safe Baseline Establishment (Pre-Flash):
  ○ Rebooted into UEFI BIOS interface.
  ○ Loaded Factory Default settings (Setup Defaults) to clear active memory XMP profiles, custom CPU overclocks, or voltage tweaks, ensuring maximum stability during flashing.
 • Phase 4 — Firmware Flash Execution (Native Utility):
  ○ Launched the motherboard's native built-in BIOS update utility (e.g., EZ Flash / Q-Flash).
  ○ Selected verified BIOS file from the FAT32 USB drive.
  ○ Initiated flash sequence under stable AC power backed by power protection infrastructure; monitored progress until automated reboot occurred.
 • Phase 5 — Post-Flash Configuration Restoration:
  ○ Re-entered UEFI BIOS post-reboot.
  ○ Re-enabled custom performance and security baselines:
   § DDR4 XMP Memory Profile
   § Secure Boot & TPM 2.0
   § Disabled CSM (Legacy Storage) to enforce pure UEFI mode
   § Enabled Above 4G Decoding & Resizable BAR (PCIe acceleration)
 • Phase 6 — Boot & Stability Validation:
  ○ Saved configuration and booted into Windows 11.
  ○ Conducted multiple cold reboots and warm restarts to confirm clean POST behavior.
  ○ Executed stress benchmarks to confirm memory and PCIe bus stability.
4. Final Outcome & Post-Repair Validation
 • Clean POST and zero boot errors.
 • Windows 11 Secure Boot and TPM 2.0 verified active.
 • All SSDs recognized in GPT/UEFI mode.
 • Sustained peak CPU boost performance and memory stability confirmed.
