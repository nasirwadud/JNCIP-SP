# JNCIP-SP Hands-On Lab Portfolio

A practical Juniper service-provider networking portfolio built around the JNCIP-SP JN0-664 curriculum and production-style engineering scenarios.

This repository focuses on configuration, monitoring, controlled failures, troubleshooting, restoration, and evidence-based validation—not exam theory alone.

## Current Progress

| Technology | Status | Documentation |
|---|---|---|
| OSPF | Complete | [View OSPF lab](OSPF/README.md) |
| IS-IS | Lab in progress | Evidence will be published after final validation |
| BGP | Planned | Advanced BGP and routing-policy labs |
| Class of Service | Planned | Classification, policing, scheduling, and rewrite rules |
| IP Multicast | Planned | IGMP, PIM, RPF, RP, ASM, and SSM |
| MPLS Foundations | Planned | Supporting MPLS and label-forwarding labs |
| Layer 3 VPNs | Planned | MPLS L3VPN control plane and forwarding |
| Layer 2 VPNs | Planned | L2 circuits, BGP L2VPN, VPLS, and EVPN |
| Automation | Planned | Linux, Python, Ansible, NETCONF, and Junos automation |

## JN0-664 Alignment

The core lab roadmap follows the official Juniper JNCIP-SP exam objectives:

- OSPF
- IS-IS
- BGP
- Class of Service
- IP Multicast
- Layer 3 VPNs
- Layer 2 VPNs

Official certification outline:

https://learningportal.juniper.net/juniper/user_activity_info.aspx?id=14336

MPLS foundations and network automation are included as supporting production skills beyond the named objective categories.

## Completed OSPF Lab

The OSPF section currently contains:

- Annotated six-router multi-area topology
- Authoritative interface, addressing, area, and router-role design
- OSPF Areas 0, 1, and 2
- Area Border Router and ASBR operation
- LSA types 1, 2, 3, 4, 5, and 7
- DR and BDR operation
- SPF metrics and equal-cost paths
- Stub, totally stub, NSSA, and totally NSSA behaviour
- Route summarisation and restriction
- OSPF virtual links
- Static and aggregate route export
- OSPF routing-policy verification
- Area, timer, authentication, and MTU mismatch troubleshooting
- Parallel-link redundancy, failure, connectivity, and restoration testing

### OSPF Documentation

- [OSPF overview](OSPF/README.md)
- [Authoritative OSPF design](OSPF/Design/README.md)
- [Annotated topology](OSPF/Topology/00-ospf-multi-area-topology.png)
- [Configuration evidence](OSPF/Configurations/)
- [Verification evidence](OSPF/Verification/)
- [Troubleshooting evidence](OSPF/Troubleshooting/)

## Engineering Workflow

Each practical lab follows the same accuracy-first workflow:

1. Define an authoritative topology and addressing plan.
2. Validate interfaces, subnets, protocol roles, and expected routing behaviour.
3. Explain each logical change before configuration.
4. Apply one logical change at a time.
5. Review configuration differences before committing.
6. Verify adjacencies, databases, routes, forwarding paths, and reachability.
7. Introduce controlled failures and capture the symptoms.
8. Diagnose from the physical layer upward using read-only commands first.
9. Record the root cause, correction, restoration, and final validation.
10. Preserve GitHub-ready evidence throughout the lab.

## Lab Environment

- Juniper vMX routers
- Junos OS
- EVE-NG
- IPv4 service-provider routing labs
- Junos operational and configuration commands
- Linux and Git
- Python, Ansible, NETCONF, and Junos PyEZ for future automation labs

## Repository Structure

```text
JNCIP-SP/
|-- OSPF/
|-- IS-IS/
|-- BGP/
|-- MPLS/
|-- L2VPN/
|-- L3VPN/
|-- CoS/
|-- Multicast/
`-- Automation/

```

Each technology section will contain its own topology, design source of truth, configurations, verification evidence, troubleshooting scenarios, and final validation.

## Evidence Standard

Repository evidence is captured directly from the lab environment and organised to show:

- Intended design
- Configuration change
- Expected result
- Failure symptom
- Diagnostic evidence
- Root cause
- Corrective action
- Restored operation

## Disclaimer

This is an independent hands-on learning portfolio. It is not affiliated with or endorsed by Juniper Networks.
