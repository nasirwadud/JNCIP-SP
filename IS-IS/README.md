# IS-IS Multi-Level Final Lab

This section documents a six-router Juniper vMX IPv4 IS-IS lab completed as hands-on preparation for the JNCIP-SP JN0-664 track. It contains the complete numbered evidence set captured during configuration, verification, controlled failure testing, routing-policy work, DIS election, database analysis, Wireshark inspection, and final restoration.

## Topology

![IS-IS multi-level final lab topology](Topology/00-isis-multilevel-final-lab-topology.png)

[View the authoritative design and addressing plan](Design/README.md)

## Practical Coverage

- Level 1 edge areas and a Level 2 backbone
- R2 and R5 as Level 1/Level 2 boundary routers
- Parallel Level 2 links between R2-R3 and R4-R5
- Default-route behaviour on Level 1 routers
- Equal-cost multipath and metric-based path selection
- Single-link survival, total backbone isolation, and restoration
- Selective Level 2-to-Level 1 route leaking with the down bit
- Level 1-to-Level 2 summarisation and suppression of specifics
- DIS priority, election, and pseudonode behaviour
- Narrow and wide metric operation
- IIH, CSNP, LSP, TLV 22, and extended reachability analysis in Wireshark
- Final adjacency, routing, and reachability validation

## Complete Evidence Sequence

### Baseline Adjacencies, Default Routes, and Reachability

1. [R1-R2 Level 1 adjacency](Evidence/01-r1-r2-level1-adjacency-up.png)
2. [R2 Level 1 and Level 2 adjacencies](Evidence/02-r2-l1-l2-adjacencies-up.png)
3. [R3 Level 2 adjacencies](Evidence/03-r3-level2-adjacencies-up.png)
4. [R4 Level 2 adjacencies](Evidence/04-r4-level2-adjacencies-up.png)
5. [R5 Level 1 and Level 2 adjacencies](Evidence/05-r5-l1-l2-adjacencies-up.png)
6. [R6-R5 Level 1 adjacency](Evidence/06-r6-r5-level1-adjacency-up.png)
7. [R1 IS-IS default route through R2](Evidence/07-r1-isis-default-route-via-r2.png)
8. [R6 IS-IS default route through R5](Evidence/08-r6-isis-default-route-via-r5.png)
9. [R1-to-R6 loopback reachability](Evidence/09-r1-to-r6-loopback-reachability.png)
10. [R6-to-R1 loopback reachability](Evidence/10-r6-to-r1-loopback-reachability.png)
11. [R2 ECMP toward R6](Evidence/11-r2-ecmp-to-r6-loopback.png)
12. [R5 ECMP toward R1](Evidence/12-r5-ecmp-to-r1-loopback.png)

### Metric Manipulation and Parallel-Link Failure

13. [Configure Level 2 metric 30](Evidence/13-r2-l2-metric-30-show-compare.png)
14. [ECMP removed by unequal metric](Evidence/14-r2-ecmp-removed-after-metric-change.png)
15. [Restore the default metric](Evidence/15-r2-restore-default-metric-show-compare.png)
16. [ECMP restored after metric reset](Evidence/16-r2-ecmp-restored-after-metric-reset.png)
17. [Deactivate the secondary IS-IS link](Evidence/17-r2-deactivate-secondary-isis-link-show-compare.png)
18. [Single Level 2 adjacency after link failure](Evidence/18-r2-single-l2-adjacency-after-link-disable.png)
19. [Single path toward R6 after link failure](Evidence/19-r2-single-path-to-r6-after-link-disable.png)
20. [Reachability over the surviving link](Evidence/20-r1-to-r6-reachability-during-single-link-failure.png)
21. [Reactivate the secondary IS-IS link](Evidence/21-r2-reactivate-secondary-isis-link-show-compare.png)
22. [Dual Level 2 adjacencies restored](Evidence/22-r2-dual-l2-adjacencies-restored.png)
23. [Deactivate both R2-R3 Level 2 links](Evidence/23-r2-both-l2-links-deactivated-show-compare.png)
24. [R1 default withdrawal and reachability failure](Evidence/24-r1-default-withdrawal-and-reachability-failure.png)
25. [R1 default route and reachability restored](Evidence/25-r1-default-route-and-reachability-restored.png)

### Packet Analysis and Link-State Database

26. [Level 2 IIH and CSNP capture](Evidence/26-wireshark-r2-r3-level2-iih-and-csnp.png)
27. [Level 2 CSNP and LSP summary](Evidence/27-wireshark-r2-level2-csnp-lsp-summary.png)
28. [R5 Level 1 and Level 2 LSP database](Evidence/28-r5-level1-level2-lsp-database-summary.png)

### Routing Policy, Route Leaking, and Summarisation

29. [R5 selective Level 2-to-Level 1 policy](Evidence/29-r5-selective-l2-to-l1-policy-show-compare.png)
30. [R6 before and after the selective route leak](Evidence/30-r6-before-after-selective-l2-to-l1-route-leak.png)
31. [Leaked prefix and down bit in the Level 1 LSP](Evidence/31-r6-r5-level1-lsp-leaked-prefix-down-bit.png)
32. [R2 Level 1-to-Level 2 summary policy](Evidence/32-r2-l1-to-l2-summary-policy-show-compare.png)
33. [R3 before and after summarisation](Evidence/33-r3-before-after-l1-to-l2-summarisation.png)
34. [Forwarding through the IS-IS summary](Evidence/34-r3-to-r1-forwarding-through-isis-summary.png)

### DIS Election and Wide Metrics

35. [Baseline: R6 is the Level 1 DIS](Evidence/35-r5-baseline-r6-level1-dis.png)
36. [R5 priority 100 and DIS election](Evidence/36-r5-priority-100-level1-dis-election.png)
37. [DIS election and pseudonode transition](Evidence/37-r5-dis-election-and-pseudonode-transition.png)
38. [R2 wide metric 100 and path selection](Evidence/38-r2-wide-metric-100-and-path-selection.png)
39. [Wireshark LSP wide metric in TLV 22](Evidence/39-wireshark-r2-level2-lsp-wide-metric-tlv22.png)

### Final Configuration and Validation

40. [R2 wide metrics and summary aggregate configuration](Evidence/40-r2-wide-metrics-and-summary-aggregate-configuration.png)
41. [R2 summary policy and export configuration](Evidence/41-r2-summary-policy-and-export-configuration.png)
42. [R5 route-leaking policy and DIS priority configuration](Evidence/42-r5-route-leaking-policy-and-dis-priority-configuration.png)
43. [R1 summary source-prefix configuration](Evidence/43-r1-summary-source-prefixes-loopback-configuration.png)
44. [Final R2 adjacencies and ECMP restored](Evidence/44-r2-final-adjacencies-and-ecmp-restored.png)

## Key Results

- All intended Level 1 and Level 2 adjacencies reached `Up` state.
- R1 and R6 learned IS-IS default routes through their nearest L1/L2 boundary routers.
- Equal link metrics produced ECMP; an unequal metric selected the lower-cost path.
- Failure of one parallel link preserved end-to-end reachability.
- Failure of both R2-R3 links withdrew R1's interarea exit and caused the expected reachability failure.
- Restoration returned the adjacencies, default route, ECMP, and sourced-ping success.
- R5 selectively leaked `3.3.3.3/32` from Level 2 into Level 1, with the down bit visible in the LSP.
- R2 advertised `172.16.0.0/22` into Level 2 while suppressing the Level 1 specifics.
- R5 won the Level 1 DIS election after its priority was raised to 100.
- Wireshark confirmed Level 2 IIH, CSNP, LSP, TLV 22, and wide-metric behaviour.

## Evidence Count

The publication contains exactly **45 numbered images**: one topology diagram (`00`) and 44 lab evidence screenshots (`01`-`44`).

## Status

The practical IS-IS final-lab configuration, controlled testing, packet capture, routing-policy, and evidence-publication phases are complete.

## Disclaimer

This is an independent hands-on learning lab. It is not affiliated with or endorsed by Juniper Networks.
