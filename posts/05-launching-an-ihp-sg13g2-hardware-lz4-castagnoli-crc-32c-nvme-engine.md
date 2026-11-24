---
id: 5-launching-an-ihp-sg13g2-hardware-lz4-castagnoli-crc-32c-nvme-engine
featured: false
title: Launching an IHP SG13G2 Hardware LZ4 + Castagnoli CRC-32C NVMe Engine
excerpt: category: RTL-to-GDSII
category: IP Verification
date: Nov 24, 2026
readTime: 1 min read
---

category: RTL-to-GDSII
excerpt: Building and hardening a 32-bit AXI4-Stream LZ4 rolling-hash match engine + single-cycle Castagnoli CRC-32C datapath on IHP SG13G2 via LibreLane.
featured: true
---
As Launch #2 of our Open-Source Silicon Series, [ihp-sg13g2-lz4-nvme-engine](https://github.com/nk-verif-labs/ihp-sg13g2-lz4-nvme-engine) pairs a hardware **LZ4 rolling-hash match engine** with a single-cycle **Castagnoli CRC-32C (`0x82F63B78`)** integrity datapath over 32-bit AXI4-Stream.

### Physical Design & CI Signoff
- **PDK & Flow:** IHP SG13G2 (130nm BiCMOS) via Nix + LibreLane (`50 MHz`, `45%` utilization).
- **Verification:** Cocotb RTL + post-PnR Gate-Level regressions passing in GitHub Actions CI ([run 45130706417](https://github.com/nk-verif-labs/ihp-sg13g2-lz4-nvme-engine/actions/runs/45130706417)).
