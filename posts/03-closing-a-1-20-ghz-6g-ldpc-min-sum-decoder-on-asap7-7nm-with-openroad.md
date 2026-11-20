---
id: 3-closing-a-1-20-ghz-6g-ldpc-min-sum-decoder-on-asap7-7nm-with-openroad
featured: false
title: Closing a 1.20 GHz 6G LDPC Min-Sum Decoder on ASAP7 7nm with OpenROAD
excerpt: category: RTL-to-GDSII
category: IP Verification
date: Nov 20, 2026
readTime: 1 min read
---

category: RTL-to-GDSII
excerpt: How we closed a (12,6) QC-LDPC Normalized Min-Sum decoder at 1.203 GHz (+125 ps setup slack, 0 hold, LEC PASS) on ASAP7 7nm.
featured: true
---
We closed [asap7-6g-ldpc-decoder](https://github.com/nk-verif-labs/asap7-6g-ldpc-decoder) on the **ASAP7 7nm FinFET** predictive PDK using OpenROAD-flow-scripts:

- **Timing & Power:** Closed `1.203 GHz` (`831.22 ps` period, `+125.04 ps` setup slack, `0` hold violations) at `3.11 mW` (`0.31%` VDD IR drop).
- **Physical Signoff:** `6,384` cells, `52%` utilization, `0` routing DRC, `0` antenna violations, and Post-CTS + Post-Route LEC PASS.
- **Verification:** Cocotb 1.9.2 (Icarus 12.0 & Verilator 5.020) `16/16` frames PASS in GitHub Actions CI (`44603626017`).
