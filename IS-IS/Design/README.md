# IS-IS Multi-Level Lab Design

This document records the source of truth used for the six-router IPv4 IS-IS final lab.

## Topology

![IS-IS multi-level final lab topology](../Topology/00-isis-multilevel-final-lab-topology.png)

## Router Roles

| Router | Loopback | IS-IS role | Area identifier shown in the lab |
|---|---:|---|---|
| R1 | 1.1.1.1/32 | Level 1 | 49.0001 |
| R2 | 2.2.2.2/32 | Level 1/Level 2 boundary router | 49.0001 |
| R3 | 3.3.3.3/32 | Level 2 | 49.0002 |
| R4 | 4.4.4.4/32 | Level 2 | 49.0002 |
| R5 | 5.5.5.5/32 | Level 1/Level 2 boundary router | 49.0002 |
| R6 | 6.6.6.6/32 | Level 1 | 49.0002 |

## Interface and Addressing Plan

| Link | Local endpoint | IPv4 address | Remote endpoint | IPv4 address | IS-IS level |
|---|---|---:|---|---:|---|
| R1-R2 | R1 `ge-0/0/0.0` | 10.10.12.1/24 | R2 `ge-0/0/0.0` | 10.10.12.2/24 | Level 1 |
| R2-R3 primary | R2 `ge-0/0/1.0` | 10.10.23.2/24 | R3 `ge-0/0/1.0` | 10.10.23.3/24 | Level 2 |
| R2-R3 secondary | R2 `ge-0/0/2.0` | 10.10.123.2/24 | R3 `ge-0/0/2.0` | 10.10.123.3/24 | Level 2 |
| R3-R4 | R3 `ge-0/0/3.0` | 10.10.34.3/24 | R4 `ge-0/0/3.0` | 10.10.34.4/24 | Level 2 |
| R4-R5 primary | R4 `ge-0/0/1.0` | 10.10.45.4/24 | R5 `ge-0/0/1.0` | 10.10.45.5/24 | Level 2 |
| R4-R5 secondary | R4 `ge-0/0/2.0` | 10.10.145.4/24 | R5 `ge-0/0/2.0` | 10.10.145.5/24 | Level 2 |
| R5-R6 | R5 `ge-0/0/0.0` | 10.10.56.5/24 | R6 `ge-0/0/0.0` | 10.10.56.6/24 | Level 1 |

## Expected Adjacencies

| Router | Interface | Neighbour | Level | Expected state |
|---|---|---|---:|---|
| R1 | ge-0/0/0.0 | R2 | 1 | Up |
| R2 | ge-0/0/0.0 | R1 | 1 | Up |
| R2 | ge-0/0/1.0 | R3 | 2 | Up |
| R2 | ge-0/0/2.0 | R3 | 2 | Up |
| R3 | ge-0/0/3.0 | R4 | 2 | Up |
| R4 | ge-0/0/1.0 | R5 | 2 | Up |
| R4 | ge-0/0/2.0 | R5 | 2 | Up |
| R5 | ge-0/0/0.0 | R6 | 1 | Up |

## Route-Propagation Design

- R1 and R6 use IS-IS default routes toward their nearest attached L1/L2 routers.
- R2 and R5 exchange Level 2 reachability through R3 and R4.
- Equal metrics on the parallel Level 2 links permit ECMP.
- Unequal metrics select the lower-cost link without destroying the adjacency.
- R2 originates aggregate `172.16.0.0/22` into Level 2 and suppresses the contributing Level 1 specifics.
- R5 selectively leaks `3.3.3.3/32` from Level 2 into Level 1.

## Design Validation

- R1 and R2 share area `49.0001`, allowing their Level 1 adjacency.
- R5 and R6 share area `49.0002`, allowing their Level 1 adjacency.
- The Level 2 backbone links can form between routers regardless of their area identifiers.
- Every point-to-point connection uses a unique `/24` IPv4 subnet.
- The two R2-R3 links and two R4-R5 links provide independent equal-cost paths.
- R2 and R5 provide the Level 1-to-Level 2 boundary function for their attached Level 1 routers.

## Controlled Tests

1. Verify all Level 1 and Level 2 adjacencies.
2. Verify Level 1 default routes and bidirectional sourced pings.
3. Verify ECMP across both parallel-link pairs.
4. Manipulate the R2-R3 metric and verify path selection and restoration.
5. Disable one R2-R3 link and verify surviving-path reachability.
6. Disable both R2-R3 links and verify default-route and reachability loss.
7. Restore both links and verify final recovery.
8. Verify selective Level 2-to-Level 1 route leaking and the down bit.
9. Verify Level 1-to-Level 2 summarisation and suppression.
10. Verify DIS election and pseudonode generation.
11. Verify wide-metric advertisement in TLV 22 using Wireshark.

## Evidence Integrity

The complete numbered evidence sequence is preserved under `Evidence/`. The final screenshot proves restored R2 adjacencies and ECMP after the controlled tests.
