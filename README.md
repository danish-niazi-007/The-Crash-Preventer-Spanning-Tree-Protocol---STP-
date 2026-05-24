🛡️ Layer 2 Loop Prevention & Mitigation (Spanning Tree Protocol)

📝 Project Overview
In enterprise network architectures, redundant links are essential to ensure High Availability (HA) and eliminate Single Points of Failure (SPOF). However, physical redundancy in switches inherently causes Layer 2 loops, leading to catastrophic **Broadcast Storms**, **MAC Table Flapping**, and **CPU Overload**.

This project is a hands-on simulation designed in **Cisco Packet Tracer** to demonstrate how the **Spanning Tree Protocol (IEEE 802.1D STP)** dynamically identifies and blocks redundant paths to maintain a loop-free topology while ensuring backup links remain ready for automatic failover.

🏗️ Network Topology
 **Devices:** 3x Cisco Catalyst 2960 Switches (`Switch0`, `Switch1`, `Switch2`)
 **Interconnections:** Copper Cross-Over cables forming a physical triangular loop.
 **Architecture:** A core switching fabric where all switches are connected to each other to provide physical redundancy.

🎯 Objectives Achieved
1. **Broadcast Storm Observation:** Analyzed how uncontrolled broadcast packets loop infinitely in a redundant Layer 2 environment.
2. **STP Root Bridge Election:** Overrode the default automatic root bridge selection (which relies on the lowest MAC address) to deterministically assign the Master Boss (Root Bridge) using CLI.
3. **Port Role Assignment:** Observed how STP calculates path costs and assigns roles (`Designated`, `Root`, and `Alternate/Blocked`).
4. **Failover Testing:** Simulated a fiber/cable cut to verify STP's automatic convergence (from Blocking -> Listening -> Learning -> Forwarding).

🛠️ Tools & Technologies
 **Simulation Engine:** Cisco Packet Tracer
 **Environment:** Cisco IOS CLI
 **Protocols:** Spanning Tree Protocol (STP), ARP, ICMP

⚙️ Configuration Commands Used
To manually elect the Root Bridge (e.g., on `Switch0`), the following administrative command was applied to lower its priority and force the election:
```text
enable
configure terminal
spanning-tree vlan 1 priority 4096
exit
