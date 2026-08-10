# IS-IS - JNCIP-SP Hands-On Lab

This section documents my practical IS-IS lab work for the Juniper Networks JNCIP-SP certification track.

The repository contains configuration evidence, verification outputs, controlled failure testing, troubleshooting results, packet analysis, routing-policy work, and restoration checks from a six-router multi-level Junos IS-IS lab.

## Lab Environment

- Juniper vMX routers
- Junos OS
- EVE-NG
- Six-router topology
- Multi-level IS-IS with Level 1, Level 2, and Level 1/Level 2 routers
- IPv4 routing
- Wireshark packet analysis
- Junos operational and configuration commands

## JN0-664 Alignment

This lab is based on the IS-IS objectives published by Juniper Networks for the JNCIP-SP JN0-664 exam.

Official exam objectives:

https://www.juniper.net/gb/en/training/certification/tracks/service-provider-routing-switching/jncip-sp.html

The evidence demonstrates practical IPv4 IS-IS operation. No unsupported production-network experience is claimed.

## Topology

![IS-IS multi-level final lab topology](Topology/00-isis-multilevel-final-lab-topology.png)

- [View the authoritative lab design](Design/README.md)
- [View the topology description](Topology/README.md)

## Practical Evidence Captured

The screenshots in this repository directly demonstrate:

- Level 1 adjacency formation on the R1-R2 and R5-R6 links
- Level 2 backbone adjacency formation across R2, R3, R4, and R5
- R2 and R5 Level 1/Level 2 boundary-router operation
- Level 1 default routes through the nearest Level 1/Level 2 router
- Bidirectional sourced-loopback reachability
- Equal-cost multipath across parallel Level 2 links
- Metric-based path selection and ECMP restoration
- Level 1 and Level 2 link-state database inspection
- Selective Level 2-to-Level 1 route leaking and the down bit
- Level 1-to-Level 2 summarisation and suppression of specifics
- DIS priority, election, and pseudonode behaviour
- Narrow and wide metric operation
- IIH, CSNP, LSP, TLV 22, and extended reachability analysis
- Final adjacency, routing, ECMP, and reachability restoration

## Troubleshooting Evidence

Controlled failures were introduced, diagnosed, corrected, and verified for:

- Failure of one R2-R3 Level 2 link while the parallel path remained available
- Collapse from ECMP to a single surviving path
- Continued end-to-end reachability during a single-link failure
- Failure of both R2-R3 links
- Withdrawal of the R1 Level 1 default route during backbone isolation
- Expected end-to-end reachability failure during total isolation
- Reactivation of both links and restoration of adjacency, routing, and connectivity

Each troubleshooting sequence preserves the configuration change, observed symptom, forwarding result, corrective action, and restored state.

## Packet Analysis Evidence

Wireshark captures verify:

- Level 2 IS-IS Hello packets
- CSNP operation and LSP summaries
- Level 2 LSP contents
- Extended IS reachability in TLV 22
- Wide-metric advertisement behaviour

## Repository Structure

```text
IS-IS/
|-- README.md
|-- Topology/
|-- Design/
|-- Configurations/
|-- Verification/
`-- Troubleshooting/
```

## Evidence Navigation

- [Configuration evidence](Configurations/)
- [Verification and Wireshark evidence](Verification/)
- [Troubleshooting and restoration evidence](Troubleshooting/)
- [Authoritative design](Design/README.md)
- [Annotated topology](Topology/00-isis-multilevel-final-lab-topology.png)

## Key Results

- All intended Level 1 and Level 2 adjacencies reached `Up` state.
- R1 and R6 learned IS-IS default routes through their nearest Level 1/Level 2 routers.
- Equal link metrics produced ECMP; unequal metrics selected the lower-cost path.
- One parallel-link failure preserved end-to-end reachability.
- Failure of both R2-R3 links withdrew R1's interarea exit and caused the expected reachability failure.
- Restoration returned the adjacencies, default route, ECMP, and sourced-ping success.
- R5 selectively leaked `3.3.3.3/32` from Level 2 into Level 1 with the down bit visible.
- R2 advertised `172.16.0.0/22` into Level 2 while suppressing the Level 1 specifics.
- R5 won the Level 1 DIS election after its priority was raised to 100.
- Wireshark confirmed Level 2 IIH, CSNP, LSP, TLV 22, and wide-metric behaviour.

## Methodology

The lab follows an accuracy-first engineering workflow:

1. Define and validate the topology, interface addressing, NETs, and IS-IS levels.
2. Explain each logical change before configuration.
3. Review configuration differences before committing.
4. Verify adjacencies, databases, routes, forwarding paths, and reachability.
5. Introduce one controlled failure at a time.
6. Diagnose using read-only operational evidence before changing configuration.
7. Record the failure, root cause, correction, restoration, and final validation.

## Status

The IPv4 IS-IS practical lab and evidence-capture phase is complete.

The repository contains 44 numbered evidence screenshots, one annotated topology diagram, and an authoritative design document covering configuration, verification, routing policy, packet analysis, redundancy, troubleshooting, and restoration.

## Disclaimer

This is an independent hands-on learning lab. It is not affiliated with or endorsed by Juniper Networks.
