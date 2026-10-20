🎫 macOS Continuity Cellular Handshake & SIP Call Relay Recovery
Ticket Header & Metadata
 • Ticket ID: SYS-MODERN-SYSINT-2026-07-19-CONTINUITY-04.V1.NotebookLM.Mac.Manual
 • Title: macOS Continuity Cellular Handshake Failure — Multi-Layer Ecosystem Diagnostics & Token Deconfliction
 • Classification: Operating System Hardening / Interoperability / Network Protocol Triage
 • Target Endpoint Mapping: EP-MAC-01 (ARM64 Apple Silicon | macOS 15+ Enterprise Hardened Profile) & iOS 18+ Core Mobile Endpoint
 • Execution Date: 19 July 2026
 • Status: 🟢 Completed / Established Baseline (Phase: Production-Ready Deployment)
 • Objective: Eliminate outbound cellular call drops and Session Initiation Protocol (SIP) relay failures on EP-MAC-01 by clearing cryptographic identity token race conditions, flushing network daemons, and deploying a dual-tier firewall architecture.
 • Definition of Done: Complete purging of stale user-space .plist identity tokens, re-alignment of 1:1 FaceTime addressing schemas, execution of privileged daemon restarts (identityservicesd, avconferenced), and verification of outbound call completion under kernel-level pf stealth rules.
 • Constraints: Must maintain strict multi-profile isolation (Admin vs. Standard UID 501); preserve biometric boundaries inside the Secure Enclave; avoid disabling global outbound process monitoring via LuLu.
 • Risks / Dependencies: Stale Apple Push Notification service (APNs) cloud tokens persisting across Apple ID key-value servers; improper pf syntax locking local loopback sockets.
 • Current Next Step: Monitor local subnet mDNS broadcast stability across daily driver sessions.
 • Evidence / Commands: Terminal outputs for sudo killall -9 identityservicesd avconferenced, sudo pfctl -e, and preference file deletion paths in ~/Library/Preferences/.
 • Result: Outbound cellular call origination restored 100%, Universal Clipboard functional, and network stealth verified via ICMP ping drop.

Executive Summary & Technical Context
Operating a multi-profile macOS environment (Administrator vs. Standard User UID 501) enforces least-privilege security but can introduce token race conditions across Apple’s Identity Services (IDS) daemon. Following initial system staging, EP-MAC-01 exhibited an asymmetrical failure pattern: inbound bridged cellular calls terminated cleanly, but outbound call originations via native UI controls aborted instantly.
Deep diagnostic triage revealed two distinct root causes:
 1. Cryptographic Token Race Condition: Concurrent identity broadcasting from both the Admin and Standard user space created duplicate hardware token entries on the paired iOS device (Settings > Apps > Phone > Calls on Other Devices), causing Apple's IDS relay to reject outbound SIP handshakes.
 2. Socket Interception Conflict: Running the native macOS Application Firewall alongside process-level outbound monitors (LuLu) blocked unsolicited local mDNS/Bonjour UDP traffic (UDP 5353) and IPsec peer-to-peer signaling required by avconferenced and sharingd.
The resolution involved purging stale local configuration caches, enforcing a 1:1 matching email address schema across devices, and replacing the stock GUI firewall with native kernel-level OpenBSD Packet Filter (pf) rules.

Detailed Step-by-Step Implementation Phases
Phase 1: Multi-Profile Identity & Secure Enclave Isolation
 1. Host Broadcaster Re-indexing: Re-indexed the localized environment broadcast string under System Settings > General > About to force an iCloud directory refresh.
 2. Secure Enclave Biometric Boundary Check: Verified that Touch ID biometrics strictly restrict duplicate fingerprint mappings across separate Unix UIDs (UID 501 Standard vs. Admin), ensuring hardware cryptographic isolation.
 3. Admin Token De-registration: Switched to the local Administrator profile, toggled "Calls from iPhone" to OFF in FaceTime settings, and signed out of the Apple Account to sever duplicate local broadcasting tokens.
Phase 2: Privileged Daemon Reset & Kernel Cache Flush
 1. Privileged Terminal Execution: Executed elevated process terminations to force launchd to restart root-owned communication daemons with clean PIDs:
sudo killall -9 identityservicesd avconferenced
sudo killall -9 sharingd bluetoothd
 2. Safe Mode Cache Purge: Booted EP-MAC-01 into Apple Silicon Safe Mode (holding physical Power button -> Shift -> Continue) to purge dynamic loader shared caches and kernel extension caches.
Phase 3: Cryptographic Cache & Preference Purification
Targeted corrupt user-space preference files in ~/Library/Preferences/ causing token race conditions:

# Delete corrupt identity and telephony plist configurations

rm ~/Library/Preferences/com.apple.FaceTime.plist
rm ~/Library/Preferences/com.apple.identityservicesd.plist
rm ~/Library/Preferences/com.apple.TelephonyUtilities.plist
rm ~/Library/Preferences/com.apple.ids.service.com.apple.private.alloy.phonecontinuity.plist

# Flush system Bluetooth and Network Interface configurations

sudo rm /Library/Preferences/com.apple.Bluetooth.plist
sudo rm /Library/Preferences/SystemConfiguration/preferences.plist
sudo rm /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist
Phase 4: Identity Addressing Alignment & Relay Re-binding
 1. iOS Relay Reset: On iOS, navigated to Settings > Apps > Phone > Calls on Other Devices, toggled the master switch OFF for 10 seconds, and re-enabled it.
 2. 1:1 Addressing Schema Verification: Aligned the "Start New Calls From" addressing rules on both endpoints to prevent SIP handshake verification failures:
  ○ On iOS: Settings > Apps > FaceTime > Start New Calls From -> Set explicitly to Apple Account Email.
  ○ On EP-MAC-01: FaceTime > Settings > Start new calls from -> Set explicitly to identical Apple Account Email.
Phase 5: Kernel-Level Packet Filter (pf) Hardening
 1. Disabled the native Application Firewall to eliminate socket interception.
 2. Created a custom anchor /etc/pf.anchors/custom.security to permit stateful outbound connections and trusted LAN traffic (mDNS/UDP) while dropping uninvited inbound probes:
pass quick on lo0 all
pass out proto { tcp udp icmp } all keep state
pass in quick from 192.168.1.0/24 to any
block in quick all
 3. Enabled session stealth mode to drop unsolicited ICMP pings:
sudo pfctl -e
echo "block in quick proto icmp" | sudo pfctl -f -
