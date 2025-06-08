# MultiArea-OSPF-DHCP-Network-Lab
![Network Topology Diagram](https://github.com/MMostafizurR/MultiArea-OSPF-DHCP-Network-Lab/blob/e339e078a4542de2f07d083e142e61fa965006a8/Full%20Image%20of%20Cisco%20Packet%20Tracer%20Lab.png "Overall Network Design")
Multi-Area OSPF & DHCP Network Design
This repository showcases a comprehensive multi-area OSPF network design implemented in Cisco Packet Tracer. It demonstrates scalable routing across multiple OSPF areas (Area 0, 10, 20, 30) using Area Border Routers (ABRs), alongside the integration of centralized DHCP services via DHCP Relay Agents for efficient IP address management.

Cisco Packet Tracer Lab Overview
This project provides a fully functional and detailed Cisco Packet Tracer lab environment, designed to demonstrate and explore advanced routing and essential network services.

The core of this lab is a multi-area OSPF (Open Shortest Path First) routing domain. It meticulously segments the network into a robust OSPF Area 0 (backbone), connecting three distinct non-backbone areas: Area 10, Area 20, and Area 30. This hierarchical design is implemented using Cisco routers configured as Area Border Routers (ABRs), showcasing how to scale OSPF and reduce routing table complexity efficiently.

![Network Topology Diagram](https://github.com/MMostafizurR/MultiArea-OSPF-DHCP-Network-Lab/blob/e339e078a4542de2f07d083e142e61fa965006a8/DHCP%20Server%20Configuration.png "DHCP Server Configuration")

Beyond routing, the lab integrates critical network services. A centralized DHCP server is deployed to dynamically assign IP addresses to end-user devices. To ensure seamless connectivity for clients across different network segments, DHCP Relay Agents (ip helper-address) are meticulously configured on the routers, forwarding DHCP requests to the central server.
![Network Topology Diagram](https://github.com/MMostafizurR/MultiArea-OSPF-DHCP-Network-Lab/blob/e339e078a4542de2f07d083e142e61fa965006a8/DHCP%20Server%20IP.png "DHCP Server IP")

Why OSPF for this Project?
OSPF was chosen for this network design due to its suitability for complex and scalable enterprise environments. Key reasons include:

Scalability: OSPF's multi-area design allows for large networks to be broken down into smaller, manageable areas, which was crucial for simulating a network with several distinct departments and locations.

Fast Convergence: OSPF quickly adapts to network changes (e.g., link failures), ensuring minimal downtime and efficient traffic redirection.

Loop-Free Routing: OSPF's SPF (Shortest Path First) algorithm inherently calculates loop-free paths, providing robust and reliable routing.

VLSM/CIDR Support: OSPF fully supports Variable Length Subnet Masking (VLSM) and Classless Inter-Domain Routing (CIDR), enabling efficient use of IP address space, which is evident in the diverse subnet sizes used in this project.

Vendor Neutrality: While implemented on Cisco, OSPF is an open standard, making it compatible across various vendors' equipment.

Advantages of OSPF in this Project
Reduced Routing Table Size: By segmenting the network into areas, ABRs summarize routes before advertising them into other areas, significantly reducing the size of routing tables on routers within those areas. This improves performance and reduces memory usage.

Faster Convergence within Areas: Link-state changes are localized within their specific area. If a link fails in Area 10, only routers within Area 10 immediately need to re-run SPF calculations, minimizing the impact on the entire backbone or other areas.

Hierarchical Design & Manageability: The multi-area structure makes the network easier to understand, manage, and troubleshoot. Different teams can manage their respective areas independently.

Optimal Path Selection: OSPF calculates the shortest path based on link costs, ensuring efficient data forwarding across the network.

Disadvantages of OSPF in this Project
Complexity: Compared to simpler routing protocols (like RIP), OSPF configuration and troubleshooting can be more complex, especially in a multi-area design.

Resource Intensive: Link-state protocols like OSPF require more CPU and memory resources on routers to build and maintain the link-state database (LSDB) and run SPF calculations.

Area 0 Requirement: All non-backbone areas must connect to Area 0. This can sometimes lead to less flexible designs if a direct physical connection isn't feasible, requiring virtual links (though not explicitly used in this current topology for inter-area connectivity).

Initial Configuration Overhead: Setting up OSPF, especially in a multi-area environment with ABRs and specific network commands, requires careful planning and execution.

How OSPF Protocol Works (Simple Explanation)
OSPF is a link-state routing protocol that allows routers to determine the best path for data to travel across a network. Here's a simplified breakdown:

Hello Packets: OSPF routers on directly connected segments send out "Hello" packets to discover and establish relationships (called adjacencies) with neighboring OSPF routers.

Link-State Advertisements (LSAs): Once neighbors are established, routers exchange small packets called LSAs. An LSA describes the router's directly connected links, their status, and their "cost" (a metric indicating bandwidth or preference).

Link-State Database (LSDB): Each router collects all LSAs from all routers within its OSPF area and compiles them into a complete "map" or topology database called the LSDB. Every router in the same area will have an identical LSDB.

SPF Algorithm: Using this LSDB, each router independently runs the Shortest Path First (SPF) algorithm (Dijkstra's algorithm). This algorithm calculates the shortest (lowest cost) path to every other destination within its area from its own perspective.

Routing Table: Based on the SPF calculation, the router builds its routing table, listing the best path to reach each network.

Multi-Area Concept: In a multi-area design, like this project, a special Area 0 (the backbone) acts as the central hub. Routers connecting Area 0 to other areas (like Area 10, 20, 30 in this project) are called Area Border Routers (ABRs). ABRs summarize routes between areas, preventing the entire network's topology from being exchanged across all areas, thus improving scalability and efficiency.

This continuous process of exchanging LSAs and running SPF ensures that all OSPF routers have an up-to-date and accurate view of the network topology, allowing for efficient and dynamic routing decisions.

![Network Topology Diagram](https://github.com/MMostafizurR/MultiArea-OSPF-DHCP-Network-Lab/blob/e339e078a4542de2f07d083e142e61fa965006a8/IP%20Configuration%20For%20each%20PC.png "IP Configuration For each PC")

Project Files:
MultiArea-OSPF-DHCP-Network-Lab.pkt The Cisco Packet Tracer file contains the complete network topology and configurations.

Router_Configurations_Scripts/: A folder containing individual .txt configuration scripts for each router (R1-R6). These files allow for quick, direct pasting of configurations into Cisco routers, facilitating easy setup, replication, and testing of the OSPF and DHCP Relay configurations within the Packet Tracer environment.

Project_Guide.pdf: A comprehensive guide for the project, including the detailed network topology diagram, complete router configurations, and essential setup/verification steps for the Cisco Packet Tracer lab.

![Network Topology Diagram](https://github.com/MMostafizurR/MultiArea-OSPF-DHCP-Network-Lab/blob/e339e078a4542de2f07d083e142e61fa965006a8/Ping%20PC1%20to%20PC6.png "Ping PC1 to PC6")

