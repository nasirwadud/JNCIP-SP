# OSPF - JNCIP-SP Hands-On Labs

This section documents my practical OSPF lab work for the Juniper Networks JNCIP-SP certification track.

The repository contains configuration evidence, verification outputs, controlled failure testing, troubleshooting results, and restoration checks from a multi-area Junos OSPF lab.

## Lab Environment

- Juniper vMX routers
- Junos OS
- EVE-NG
- Six-router topology
- Multi-area OSPFv2
- IPv4 routing
- Junos operational and configuration commands

## JN0-664 Alignment

This lab is based on the OSPF objectives published by Juniper Networks for the JNCIP-SP JN0-664 exam.

Official exam objectives:

https://www.juniper.net/gb/en/training/certification/tracks/service-provider-routing-switching/jncip-sp.html

The screenshots below provide practical OSPFv2 evidence for the objectives demonstrated in this lab. OSPFv3 is covered separately as theory and is not claimed as practical evidence.

## Practical Evidence Captured

The screenshots in this repository directly demonstrate:

- Baseline OSPF neighbour formation on R2
- Multi-area OSPF operation on R2 and R3
- Area Border Router operation
- DR and BDR operation
- OSPF database visibility across Areas 0, 1, and 2
- LSA types 1, 2, 3, 4, 5, and 7
- SPF path selection and metric changes
- Equal-cost multipath routing and restoration
- OSPF external E1 and E2 routes
- Area route summarisation
- Route-summary restriction and restoration
- OSPF virtual-link operation and removal
- OSPF export-policy configuration
- Static-route export into OSPF
- Aggregate-route export into OSPF
- Rejection of unmatched static routes

## Troubleshooting Evidence

Controlled failures were introduced, diagnosed, corrected, and verified for:

- Area mismatch
- Hello and dead timer mismatch
- Authentication mismatch
- MTU mismatch

Each troubleshooting sequence includes failure evidence, diagnostic evidence, and restored adjacency evidence.

## OSPFv2 and OSPFv3

The practical lab uses OSPFv2 for IPv4.

OSPFv2 and OSPFv3 differences are covered as theory. OSPFv3 was not configured in this lab, so no practical OSPFv3 evidence is claimed.

## Repository Structure

```text
OSPF/
|-- README.md
|-- Topology/
|-- Design/
|-- Configurations/
|-- Verification/
|-- Troubleshooting/
`-- Final-Test/
```

## Methodology

Each lab follows an accuracy-first engineering workflow:

1. Define and validate the topology.
2. Confirm interface addressing and OSPF area assignments.
3. Explain each logical change before configuration.
4. Review configuration differences before committing.
5. Verify neighbours, databases, routes, and reachability.
6. Troubleshoot failures from the physical layer upward.
7. Record the root cause, correction, and final validation.

## Status

The OSPFv2 practical evidence-capture phase is complete.

The repository currently contains 38 screenshots covering configuration, verification, routing-policy behaviour, troubleshooting, and restoration.
