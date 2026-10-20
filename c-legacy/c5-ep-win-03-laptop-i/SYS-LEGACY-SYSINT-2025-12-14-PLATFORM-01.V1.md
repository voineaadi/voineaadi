🎫Laptop I — Platform Management Software Recovery, Dependency Repair & Thermal Management Restoration
[ Task / Ticket ]
 • Ticket ID: SYS-LEGACY-SYSINT-2025-12-14-PLATFORM-01.V1.Manual.Win.Manual
 • Title: Laptop I — Platform Management Software Recovery, Dependency Repair & Thermal Management Restoration
 • Classification: Endpoint Software Remediation / Platform Stability / Performance & Thermal Management
 • Target Endpoint Mapping: EP-WIN-03 (x86_64 Intel, Windows 11 Pro, Mobile Profile — Custom Laptop I Workstation)
 • Execution Date: 14 December 2025
[ Status: 🟢 Standby / 🟡 In Progress / 🔴 Optimize ]
 • Status: 🟢 Completed / Resolved – Stable Configuration
 • Objective: Remediate platform management suite instability on Laptop I following a Windows 11 feature update that caused loss of fan curve control, temperature telemetry, and performance/overclocking profiles.
 • Definition of Done: Deep removal of legacy platform software, GPU driver cleanup via DDU, restoration of C++ / .NET runtime dependencies, clean reinstallation of OEM management suite, and verification of fan control and thermal profiles.
 • Constraints: Use DDU in Safe Mode for GPU driver purging; reinstall C++ Redistributables (2015–2022) x86 & x64; remove conflicting third-party audio software.
 • Risks / Dependencies: Hardware overheating due to stuck fan curves; GPU driver telemetry disruption breaking fan control; WMI servicing stack inconsistencies.
 • Current Next Step: Maintain runtime dependencies (.NET and Visual C++) and create restore points prior to major OS feature updates.
 • Evidence / Commands: Safe Mode DDU cleanup logs; Visual C++ installer execution logs; OEM management suite service verification in services.msc.
 • Result: Platform management software fully operational, fan profile control restored, thermal telemetry active, zero thermal throttling under high-performance gaming workloads.
 • Archive Location: OneNote / 14.4.Legacy.Laptop1.pdf / SEC-DEV-2025-10-LAPTOPI-PLATFORM

Executive Summary / Complete Context
Following a Windows 11 feature update and routine driver updates, Laptop I experienced platform management software instability that resulted in a partial loss of thermal controls, fan profile management, and performance telemetry. Root causes included Windows servicing stack changes, driver dependency mismatches, legacy software residue, GPU driver telemetry conflicts, and missing/outdated Microsoft runtime dependencies (.NET Framework & Visual C++ Redistributables). The issue was resolved through complete software cleanup, GPU driver purging via DDU, runtime dependency repair, and a structured reinstallation of the platform management suite. Full thermal control, fan profile management, and system stability were successfully restored.

Detailed Step-by-Step Technical Content

1. Environment & Asset Details
 • Device: Laptop I (High-Performance Laptop Workstation)
 • Operating System: Windows 11 Pro
 • Platform Management Suite: Generic OEM Management Suite
 • GPU Vendor: NVIDIA
 • Target Endpoint Mapping: EP-WIN-03 (Mobile Profile)
 • Usage Profile: Gaming, high-performance processing, thermal-sensitive workloads
2. Root Cause Analysis (RCA)
 1. Windows Update Servicing Stack Changes: OS servicing updates altered system components used by the management software (WMI, runtime libraries, hardware abstraction layer).
 2. Legacy Component Residue: Leftover files and registry keys caused service initialization conflicts.
 3. GPU Driver Telemetry Disruption: Corrupted GPU driver telemetry prevented the management software from reading GPU temperature and applying performance profiles.
 4. Runtime Dependency Issues: Missing or corrupted Microsoft Visual C++ Redistributables (2015–2022) and .NET Framework libraries.
 5. Conflicting Audio Enhancements: Third-party audio software interfered with management suite service bindings.
3. Step-by-Step Remediation Procedure
 • Phase 1 — Software Removal & Residue Cleanup:
  ○ Uninstalled management software using official uninstaller.
  ○ Cleared residual file folders and registry keys manually.
  ○ Verified complete service removal in services.msc.
 • Phase 2 — Version Compatibility Testing:
  ○ Tested previous management software version; identified incompatibilities and fully uninstalled it.
 • Phase 3 — Windows Component Repair:
  ○ Repaired Windows Update servicing stack.
  ○ Installed latest .NET Framework updates.
 • Phase 4 — Runtime Dependency Restoration:
  ○ Installed and repaired Microsoft Visual C++ 2015–2022 Redistributables (both x86 and x64 packages).
 • Phase 5 — GPU Driver Purge & Clean Driver Deployment:
  ○ Booted into Safe Mode and purged existing NVIDIA drivers using Display Driver Uninstaller (DDU).
  ○ Installed OEM-validated GPU drivers via NVCleanstall.
 • Phase 6 — Conflicting Component Removal:
  ○ Removed conflicting third-party audio enhancement utilities and services.
 • Phase 7 — Clean Management Suite Installation:
  ○ Installed primary management suite and supporting packages in the exact required sequence.
  ○ Verified all background services (software service, client management service, monitoring service) were active in services.msc.
4. Validation & Final System State
 • Management Suite Verification: Launched suite successfully with zero crashes.
 • Thermal & Fan Control: Verified active temperature telemetry and dynamic fan curve adjustments across all performance profiles.
 • Workload Testing: Certified stable FPS, optimal GPU utilization, and zero thermal throttling during extended gaming and stress-testing sessions.
