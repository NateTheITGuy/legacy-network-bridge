# legacy-network-bridge
Resolution of RNDIS driver conflicts to bridge mobile gateways with Windows 10 legacy environments.
Project: Legacy System Network & Driver Troubleshooting
Status: Documented Fix for RNDIS Connectivity Issues
Executive Summary
This project demonstrates the manual resolution of a driver handshake failure between a mobile gateway (Android) and a Windows 10 legacy environment. This specific issue occurs when the OS fails to recognize the mobile device as a network interface, defaulting instead to a "Charge Only" state or a generic "Unknown Device" flag.
Technical Problem
 * Symptom: USB Tethering toggle on the mobile device fails to remain active (reverts to 'Off').
 * OS Behavior: Windows Network Connections (ncpa.cpl) shows a "Network Cable Unplugged" status for the physical Ethernet port, but fails to populate a Virtual NDIS (Network Control Model) interface for the tethered device.
 * Constraint: Standard automated driver updates fail to identify the hardware ID of the mobile bridge.
Resolution Workflow (The "Fix")
To bridge the connection, a manual driver injection was required to force the OS to recognize the RNDIS protocol:
 * Hardware Verification: Confirmed data-transfer capability of the USB cable (bypassing power-only limitations).
 * Driver Injection: * Accessed Device Manager > Network Adapters.
   * Identified the "Unknown" or "Generic" USB device.
   * Manually selected: Update Driver > Browse my computer > Let me pick from a list.
   * Forced the Microsoft > Remote NDIS Compatible Device driver profile.
 * Protocol Alignment: Adjusted Windows Network Profile to Private and disabled Selective Suspend in Power Options to prevent signal throttling.
Professional Skills Demonstrated
 * Process Adherence: Systematic troubleshooting of the OSI Model (Layer 1 Physical to Layer 3 Network).
 * Documentation: Clear reporting of incident resolution for knowledge-base (KB) utilization.
 * Legacy Support: Navigating driver conflicts in older Windows 10 builds.
Next Steps for your Portfolio:
 * Upwork: Copy the "Executive Summary" and "Technical Problem" sections into your Upwork portfolio description.
