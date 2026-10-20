🎫Desktop I — Residential Power Instability Mitigation & Hardware Rebuild
[ Task / Ticket ]
 • Ticket ID: SYS-LEGACY-SYSINT-2017-08-15-STABIL-01.V1.Manual.Win.Manual
 • Title: Desktop I — Residential Power Instability Mitigation & UPS Deployment + Progressive Hardware Failure, PSU Root Cause, and System Stabilization
 • Classification: Infrastructure Risk Mitigation / Electrical Stability & Hardware Incident / PSU Failure / System Rebuild
 • Target Endpoint Mapping: EP-WIN-01 (x86_64 Intel, Windows 10/11 Pro, Standard Desktop Profile — Legacy Desktop I Workstation)
 • Execution Date: 15 August 2017 (July–August 2017; Financial Summary: August 2020)
[ Status: 🟢 Standby / 🟡 In Progress / 🔴 Optimize ]
 • Status: 🟢 Completed / Resolved — System Stabilized & Fully Functional (Archived & Reassigned)
 • Objective: Eliminate recurring random system freezes, black screens, and component degradation on Desktop I caused by Power Supply Unit (PSU) internal degradation compounded by unstable residential mains voltage in Câmpina, Romania.
 • Definition of Done: Replacement of failing PSU, installation of line-interactive AVR UPS (1500VA/900W) + servo motor stabilizer (2100VA/1200W), professional upgrade of electrical wall sockets/panel, and multi-year zero-freeze verification under load.
 • Constraints: High financial investment budget; requirement to diagnose without bench service shop false negatives; maintaining workspace electrical safety.
 • Risks / Dependencies: Unstable residential electrical mains grid; motherboard trace/capacitor thermal damage if unmitigated.
 • Current Next Step: Maintain power protection infrastructure baseline across all active endpoints (EP-WIN-01, EP-WIN-02, EP-WIN-03, EP-LIN-03).
 • Evidence / Commands: Financial investment ledger (7,277 RON breakdown); stress test logs; multi-year uptime verification post-remediation.
 • Result: Complete system stability achieved, zero subsequent freezes or black screens, electrical risk 100% neutralized; machine gifted in 100% working order.

Executive Summary / Complete Context
Desktop I experienced progressive instability characterized by random system freezes, black screens, and intermittent boot failures. Multiple core components were replaced through a structured, stepwise troubleshooting process. After extensive hardware replacements and validation cycles across alternative desktop configurations, the primary root cause was identified as a failing Power Supply Unit (PSU) compounded by unstable residential mains voltage conditions. Repeated unexplained system freezes, hardware degradation, and instability across multiple hardware configurations were ultimately correlated with inconsistent external electrical power delivery.
Following root cause validation, a line-interactive UPS with Automatic Voltage Regulation (AVR) was deployed alongside a dedicated voltage stabilizer and surge protection unit. Electrical sockets across the workspace were upgraded with professional installation and verification. This combined infrastructure remediation fully eliminated all system instability. Long-term operational reliability was achieved and sustained for years thereafter without a single recurrence. The system operated in fully stable condition and was later reassigned (gifted) while operating at peak functionality.

Detailed Step-by-Step Technical Content

1. System Environment & Deployed Protection
 • Original Platform Components:
  ○ CPU: High-performance quad-core processor
  ○ Motherboard: Standard ATX motherboard
  ○ UPS: Generic 1500VA / 900W Line-Interactive UPS with AVR
 • Location: Residential property – Câmpina, Romania
 • Systems Affected: Desktop I (Primary Workstation)
 • Power Protection Infrastructure Deployed:
  ○ Generic 1500VA / 900W Line-Interactive UPS with AVR
  ○ Generic 2100VA / 1200W Network Stabilizer with Servo Motor (Pure Sine Wave)
2. Business Impact & Risk Analysis
 • Operational Impact:
  ○ Repeated system downtime and productivity loss
  ○ High financial impact due to unnecessary component replacements
  ○ Multiple service provider visits and delayed warranty claims
  ○ Operational unpredictability during active workloads
 • Pre-Mitigation Risk Level: High
  ○ Random system freezes during active workloads
  ○ Forced hard shutdowns via physical power button
  ○ Severe hardware degradation (including motherboard capacitor failure)
  ○ Financial loss due to repetitive component swaps
 • Post-Mitigation Outcome:
  ○ Complete system stability achieved
  ○ No further unexplained freezes or black screens
  ○ Electrical infrastructure risk fully neutralized
  ○ Multi-year operational reliability confirmed
3. Observed Symptoms
 • Random full system freezes during active use (no BSOD generated).
 • Sudden black screen events and hard system locks without automatic recovery.
 • Intermittent successful boots followed by rapid instability under load.
 • Increasing instability frequency over time.
 • Burned motherboard capacitor (visible smoke observed).
 • Suspected CPU socket bending / POST inconsistencies.
 • Failure to consistently complete POST (Power-On Self-Test).
4. Root Cause Analysis (RCA)
 • Primary Root Cause: Unstable residential mains voltage delivery compounding Power Supply Unit (PSU) internal degradation.
 • Contributing Environmental Factors:
  ○ Absence of surge protection on the main electrical line.
  ○ Absence of active voltage regulation.
  ○ Direct wall-socket power connection.
  ○ Limitations and age of historical residential electrical installation.
 • Impact of Power Fluctuations: Voltage fluctuations resulted in physical capacitor damage, motherboard trace degradation, PSU internal stress, and random system memory/state corruption.
5. Initial Diagnostics
 • System transported to local IT service provider for bench testing.
 • Service conclusion: "No hardware fault identified" (due to stable voltage conditions at the service facility).
 • System returned home and appeared temporarily stable before instability resumed after a short operational period.
 • Diagnostic Lesson: No electrical instability testing was performed at the service provider's bench environment.
6. Troubleshooting Timeline (Phase 1 → Phase 4)
 • Phase 1 — Initial Hardware Swap:
  ○ Replaced motherboard, CPU, and PSU sequentially.
  ○ Tested components individually; verified video output across alternative displays.
  ○ Tested components inside alternative desktop configurations; all components were validated as functional.
  ○ System appeared temporarily stable at home, but instability subsequently returned.
 • Phase 2 — Service Provider Evaluation:
  ○ System re-transported to local IT service for extended bench testing.
  ○ No faults were reproduced in the service shop environment.
  ○ System returned home; instability resumed immediately upon connecting to residential mains.
 • Phase 3 — Warranty & RMA Execution:
  ○ Submitted motherboard under warranty; replacement unit issued by manufacturer.
  ○ Hardware reinstalled per manufacturer specifications.
  ○ BIOS configuration reviewed and initially left at default settings.
  ○ System initially failed to boot, highlighting underlying PSU degradation as a major contributing factor.
 • Phase 4 — PSU Root Cause Confirmation & Infrastructure Deployment:
  ○ Systematic elimination of GPU, RAM, CPU, and Motherboard.
  ○ Generic 750W 80+ Gold Modular PSU identified as unstable under dynamic load conditions.
  ○ Installed replacement PSU: Generic 730W 80+.
  ○ Simultaneously implemented full electrical remediation: UPS deployment, AVR implementation, surge protector installation, and residential electrical socket/panel upgrades.
7. Financial Summary & Technology Investment (August 2020 Breakdown)
Component / Infrastructure Item Cost (RON)
High-Performance CPU 1,000 RON
Quad-Core CPU Upgrade 1,000 RON
Previous Motherboard 800 RON
Replacement Motherboard 800 RON
Replacement Power Supply Unit (PSU - 730W 80+) 257 RON
Line-Interactive UPS (1500VA / 900W with AVR) 1,220 RON
Network Stabilizer with Servo Motor (2100VA / 1200W) 500 RON
Full Residential Socket & Panel Upgrade 1,000 RON
Total Technology Investment 7,277 RON
8. Step-by-Step Resolution Methodology
 1. Assessed residential electrical stability and identified mains voltage fluctuations.
 2. Purchased and deployed an AVR-enabled UPS, dedicated surge protector, and external voltage stabilizer.
 3. Evaluated servo stabilizer integration (retained as an additional protection layer behind the UPS).
 4. Routed all desktop workstations through the upgraded wall sockets, surge protector, AVR, and UPS chain.
 5. Standardized the deployment of high-quality, high-efficiency power supply units across all desktop builds.
 6. Conducted extended stress testing and monitored system behavior under sustained heavy processing loads.
9. Final Outcome & Operational Results
 • Remediation Completed: PSU replaced, UPS installed, AVR active, dedicated surge protection deployed, and residential workspace electrical sockets professionally upgraded.
 • Immediate Verification: Immediate system stabilization, complete elimination of random freezes and black screens, zero component degradation, and multi-year verified operational stability.
 • Lifecycle End State: System later reassigned (gifted) in 100% stable, fully functional condition.
10. Lessons Learned
 • PSU degradation frequently manifests as random system freezes without triggering Windows BSODs or crash dumps.
 • External electrical mains instability can perfectly mimic internal hardware component failure.
 • Bench testing in isolated service shop environments without reproducing real-world power conditions fails to identify environmental electrical faults.
 • Stepwise component replacement without evaluating input power infrastructure significantly inflates repair costs.
11. Preventive Recommendations
 • Always deploy an AVR-enabled Line-Interactive or Online UPS for high-performance desktop workstations.
 • Validate external electrical mains stability before replacing core platform components (CPU, Motherboard, GPU).
 • Avoid assuming motherboard or CPU failure without first testing PSU health under dynamic load.
 • Conduct extended load testing before declaring a repaired desktop system fully stable.
 • Modernize residential electrical infrastructure (grounding, Dedicated 2.5 mm² lines) where high-density IT equipment operates.
 • Avoid direct wall-outlet connections for sensitive desktop hardware.
 • Perform periodic UPS battery health checks and runtime recalibration cycles.
