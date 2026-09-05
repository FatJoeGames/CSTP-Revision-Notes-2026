### Deliverable A: Network Design & Build

**The Goal:** Design, assemble, configure, optimise, test, and troubleshoot a distributed network (more than one sub-net) with static and dynamic routes.

**Required Tool:** Cisco Packet Tracer.

#### Phase 1: Design (Targeting the "Merit" Grade)
To achieve a Merit for Technical Competency 2, you must provide evidence that you considered more than one design option. 
*   **Action:** Before touching Packet Tracer, draft two brief network topologies. 
*   **Option 1 (The Reject):** A flat "Hub and Spoke" network with a single subnet for all servers and clients. Explain that while simple, it fails to provide necessary security isolation for the web application.
*   **Option 2 (The Chosen Design):** A segmented architecture featuring a WAN edge, an internal Corporate LAN, and a dedicated DMZ for the file-upload server. Justify this choice as it limits the blast radius if the web server is compromised, aligning with defense-in-depth principles.

#### Phase 2: Build & Configure (Targeting the "Pass" Grade)
You need to assemble the hubs, switches, routers, and user devices to meet the design requirements.
*   **Action:** Open Cisco Packet Tracer and drag in your hardware (e.g., Cisco 1941 routers, 2960 switches, and generic server/PC endpoints).
*   **Configuration:** You must implement both static and dynamic routes across multiple subnets.

**Cisco CLI Configuration Snippets:**

*1. Setting up the Dynamic Route (OSPF):*
```text
! On Router 1 (Internal Core)
enable
configure terminal
router ospf 1
 ! Advertise the Internal LAN and the link to the DMZ Router
 network 192.168.10.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.3 area 0
 passive-interface GigabitEthernet0/0 ! Prevent OSPF hellos on the user LAN
exit
```

*2. Setting up the Static Route:*
```text
! On Router 2 (DMZ/Edge Router)
enable
configure terminal
 ! Create a default static route pointing traffic out to the simulated ISP/WAN
 ip route 0.0.0.0 0.0.0.0 203.0.113.1
exit
```

#### Phase 3: Optimise & Secure
Fine-tune the network to ensure peak efficiency and enforce security policies.
*   **Action:** Apply Access Control Lists (ACLs) to your DMZ router to ensure only permitted traffic (like HTTPS) reaches your web server, blocking everything else.

*ACL Configuration Snippet:*
```text
! Restrict traffic into the DMZ Web Server (192.168.20.50)
access-list 100 permit tcp any host 192.168.20.50 eq 443
access-list 100 deny ip any any

interface GigabitEthernet0/1
 ip access-group 100 in
```

#### Phase 4: Test & Troubleshoot (Targeting the "Distinction" Grade)
A Pass requires troubleshooting typical problems, but a Distinction requires you to troubleshoot *complex* problems in your network implementation.
*   **Action:** You need to intentionally break something subtle, fix it, and document the process in your Part A write-up.
*   **Complex Troubleshooting Idea:** Create an asymmetric routing issue or an OSPF neighbor adjacency failure (e.g., mismatched subnet masks or MTU sizes on connecting router interfaces). 
*   **Evidence Collection:** Take screenshots of the broken state (e.g., `show ip ospf neighbor` showing a stuck state), explain your diagnostic methodology using standard commands (`traceroute`, `ping`, `show ip route`), and then provide the screenshot of the resolved, fully converged routing table.
