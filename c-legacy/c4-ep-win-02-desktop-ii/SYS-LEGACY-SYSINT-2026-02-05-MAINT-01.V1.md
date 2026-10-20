🎫Desktop II — Scheduled Physical Maintenance, Internal Cleaning, and CPU Thermal Compound Replacement
[ Task / Ticket ]
 • Ticket ID: SYS-LEGACY-SYSINT-2026-02-05-MAINT-01.V1.Manual.Win.Manual
 • Title: Desktop II — Scheduled Physical Maintenance, Internal Cleaning, and CPU Thermal Compound Replacement
 • Classification: Preventive Hardware Maintenance / Thermal Optimization / Physical System Reliability
 • Target Endpoint Mapping: EP-WIN-02 (x86_64 Intel, Windows 11 Home, Standard Desktop Profile — Custom Desktop II Workstation)
 • Execution Date: 05 February 2026
[ Status: 🟢 Standby / 🟡 In Progress / 🔴 Optimize ]
 • Status: 🟢 Completed / Archived – Hardware Maintenance Successful
 • Objective: Perform semiannual preventive physical cleaning, dust removal, and proactive CPU thermal compound replacement on Desktop II to maintain optimal heat transfer efficiency and prevent thermal throttling.
 • Definition of Done: Complete internal dust removal using ESD-safe brushes and high-concentration alcohol, residue-free removal of aged thermal paste, fresh thermal compound application, and thermal/boot validation under heavy load.
 • Constraints: Complete power isolation and residual capacitor discharge prior to opening chassis; use ESD-safe tools; prevent liquid oversaturation during precision cleaning.
 • Risks / Dependencies: ESD damage to motherboard/CPU; improper thermal paste volume causing thermal spikes; cooler mounting pressure imbalance.
 • Current Next Step: Schedule the next semiannual internal cleaning cycle for August 2026.
 • Evidence / Commands: Visual inspection logs; post-maintenance thermal telemetry logs under CPU-intensive workloads.
 • Result: Thermal resistance reduced, CPU boost response optimized, internal hardware pristine, zero thermal throttling confirmed under gaming and diagnostic loads.
 • Archive Location: OneNote / 14.3.Legacy.Desktop2.pdf / SYS-DEV-2026-02.05-DESKTOPII-MAINT

Executive Summary / Complete Context
Maintenance was performed as part of a structured preventive hardware reliability program on Desktop II. The intervention was proactive and not triggered by hardware malfunction. Over time, environmental dust accumulation and thermal interface material aging can increase thermal resistance, leading to elevated CPU operating temperatures, fan noise, and potential thermal throttling under sustained heavy processing loads. A systematic physical overhaul was executed, including workspace power isolation, internal dust extraction, precision fan blade cleaning, old thermal paste removal, fresh thermal compound application, and post-maintenance thermal validation under load.

Detailed Step-by-Step Technical Content

1. Environment & Baseline Setup
 • Device: Desktop II
 • Hardware Platform: Custom Desktop Workstation
 • CPU: High-performance multi-core processor
 • Operating System: Windows 11
 • Location: Romania
 • Usage Profile: High-performance workstation, gaming, administrative/technical operations, hardware diagnostics, and tuning.
2. Business Impact & Reliability Benefits
 • Thermal Stability Improvement: Reduced thermal resistance between CPU heat spreader and cooler heatsink, optimizing heat transfer efficiency.
 • Performance Stability: Reduced thermal throttling risks, preserving sustained CPU boost clocks.
 • Hardware Longevity: Minimized long-term thermal stress on CPU VRMs and motherboard traces.
 • Operational Reliability: Eliminated emergency hardware interventions through disciplined semiannual scheduling.
3. Step-by-Step Maintenance Procedure
 • Phase 1 — Workspace Preparation and Power Isolation:
  ○ Powered down system completely.
  ○ Disconnected AC power cable and all external peripherals (keyboard, mouse, displays, Ethernet, USB, audio).
  ○ Prepared a clean, dry, ESD-safe workspace with precision lighting.
  ○ Gathered materials: ESD-safe brushes, cotton swabs/balls, ~90% medicinal alcohol, lint-free cleaning cloths.
 • Phase 2 — Internal Access and Visual Inspection:
  ○ Pressed power button briefly after disconnecting AC power to discharge residual motherboard capacitors.
  ○ Removed side panel and performed visual inspection (verified no liquid contamination, loose wires, or damaged cables).
 • Phase 3 — Internal Cleaning Procedure:
  ○ Dry Cleaning: Used ESD-safe brushes to clean dust from CPU cooler fins, chassis interior, fan blades, motherboard surfaces, and PSU air intake.
  ○ Precision Cleaning: Lightly moistened cotton swabs with ~90% alcohol to clean fan blade edges, structural metal contact points, and non-sensitive areas (ensured zero liquid oversaturation and full evaporation).
 • Phase 4 — CPU Thermal Compound Removal:
  ○ Dismounted CPU cooler assembly to expose CPU heat spreader.
  ○ Thoroughly removed aged thermal compound using alcohol-moistened swabs and lint-free cloths until the surface was completely clean and residue-free.
 • Phase 5 — Thermal Compound Application:
  ○ Applied fresh high-quality thermal compound to the center of the CPU heat spreader in correct volume.
  ○ Reinstalled CPU cooler assembly, enforcing even cross-pattern mounting screw pressure to ensure optimal contact and thermal interface integrity.
 • Phase 6 — Reassembly and Boot Validation:
  ○ Reinstalled chassis side panel, reconnected AC power and essential peripherals, and powered on the system.
4. Post-Maintenance Validation
 • Boot Validation: Normal POST behavior, clean Windows 11 boot sequence, no hardware errors.
 • Thermal Performance Validation: CPU temperatures monitored under idle, standard, and high-performance gaming/diagnostic loads; observed lower baseline idle temperatures and smooth thermal decay response post-load.
 • Stability Validation: Zero crashes, zero instability, and reduced acoustic fan profile during sustained processing.
5. Preventive Recommendations & Schedule
 • Internal Dust Cleaning: Executed every 6 months.
 • Thermal Compound Replacement: Executed proactively every 2–3 years.
 • Safety Protocols: Always discharge residual power before touching internal components; maintain ESD precautions.
