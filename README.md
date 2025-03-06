# Multi-Datacenter EVPN-VXLAN Integration with Versa Flex VNF

## Overview
This repository contains configuration files and documentation for a networking lab that demonstrates EVPN-VXLAN implementation across two datacenters. The primary datacenter uses Cisco Nexus infrastructure, while the secondary datacenter utilizes Versa Flex VNF. Both datacenters are interconnected through an MPLS backbone network.

## Network Topology
The lab consists of:
- **CISCO DC**:
  - 2 Spine switches (SPINE-DC-1, NX-SPINE-2)
  - 2 Leaf switches (NX-Leaf-1, NX-Leaf-2)
  - VLANs 10, 20, 30 for endpoint connectivity
  - AS Number: 65000

- **VERSA DC**:
  - Versa Flex VNF implementation
  - 2 Virtual spine switches (Versa-Spine-1, Versa-Spine-2)
  - 2 Virtual leaf switches (Versa-Leaf-1, Versa-Leaf-2)
  - Endpoint connectivity for multiple subnets
  - Integration with Versa SD-WAN/SASE capabilities

- **MPLS Backbone**:
  - PE routers (PE-1, P-RR, ASBR, P-2)
  - MPLS core providing transport between datacenters
  - AS Number: 65100

## Key Features
- Multi-datacenter VXLAN EVPN fabric with BGP as control plane
- L2/L3 VNI extension between Cisco infrastructure and Versa Flex VNF
- VRF segmentation and tenant isolation across datacenters
- BGP EVPN control plane for distributed learning
- Integration between physical and virtual network infrastructure
- Seamless connectivity between 172.16.x.x/24 subnets across both datacenters

## Technical Details
- VXLAN encapsulation for overlay traffic
- BGP EVPN Type-2/Type-5 routes for host/prefix advertisement
- Anycast gateway implementation for optimal traffic forwarding
- L3VNI (VLAN 999) for inter-VRF communication
- LACP-based port-channels for link redundancy
- Integration with Versa Director for management of Versa components

## Implementation Notes
- Each datacenter maintains independent underlay routing (OSPF)
- BGP EVPN provides the overlay control plane
- End-to-end connectivity is maintained for workloads in any datacenter
- Multi-tenant capability with isolated VRFs
- Advanced features like symmetric IRB for inter-VXLAN routing

## Configuration Files
- Cisco Nexus spine/leaf switch configurations
- Versa Flex VNF configurations
- PE router configurations for MPLS backbone integration

## Use Cases
- Datacenter migration scenarios
- Hybrid cloud connectivity
- Disaster recovery implementations
- Multi-site service deployment
