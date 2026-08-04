# OSPF - JNCIP-SP Hands-On Labs

This section documents my practical OSPF study and lab work for the Juniper Networks JNCIP-SP certification track.

The focus is not limited to configuration commands. Each lab includes network design, implementation, verification, failure testing, troubleshooting, and analysis of routing behaviour.

## Lab Environment

- Juniper vMX routers
- Junos OS
- EVE-NG
- Multi-area OSPF topology
- IPv4 routing
- Junos operational and configuration commands

## Topics Covered

- OSPF neighbour formation
- Backbone and non-backbone areas
- Area Border Routers
- Autonomous System Boundary Routers
- Stub areas
- Totally stub areas
- NSSA
- Totally NSSA
- Virtual links
- DR and BDR election
- OSPF authentication
- Passive interfaces
- Default route advertisement
- Route summarisation
- External route redistribution
- OSPF E1 and E2 external routes
- OSPF import and export policies
- LSA types 1, 2, 3, 4, 5, and 7
- OSPF route preference and path selection
- Multi-area reachability verification
- Troubleshooting adjacency and routing failures

## Troubleshooting Scenarios

The labs include practical investigation of:

- Area mismatch
- Hello and dead timer mismatch
- Authentication mismatch
- MTU mismatch
- Passive-interface behaviour
- Missing routes
- Incorrect route redistribution
- Default-route problems
- OSPF policy errors
- Return-path failures

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

OSPF study labs and the final practical test have been completed.

Detailed configurations, topology information, verification results, and troubleshooting cases will be added to the corresponding folders.
