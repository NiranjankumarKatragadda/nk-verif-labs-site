---
id: 4-fixing-13-93-ns-setup-violations-on-a-6-4-gbps-6g-baseband-tx-in-gf180mcu
featured: false
title: Fixing -13.93 ns Setup Violations on a 6.4 Gbps 6G Baseband TX in GF180MCU
excerpt: category: RTL-to-GDSII
category: IP Verification
date: Nov 22, 2026
readTime: 1 min read
---

category: RTL-to-GDSII
excerpt: How replacing a 16-byte unrolled CRC-32 loop with a balanced GF(2) parallel XOR tree closed 50 MHz setup timing in LibreLane on GF180MCU.
featured: true
---
Wide datapaths on 180nm processes quickly expose serial logic depth. On [gf180-6g-baseband-tx](https://github.com/nk-verif-labs/gf180-6g-baseband-tx), a 128-bit AXI4-Stream pipeline at 50 MHz (`6.4 Gbps`) spans `axis_skid_fifo`, `scrambler_128b`, `crc32_128b`, `fec_conv_enc`, and `qam_mapper_axis`.

### The Bottleneck & Fix
An initial 16-byte unrolled loop in `crc32_128b.v` failed setup timing at **`-13.93 ns` WNS**. Replacing it with a **balanced GF(2) parallel XOR tree** closed `nom_tt_025C_5v00` setup and hold timing at **`0.000 ns` WNS**.

### Sign-Off & Dual-Sim CI
- **Physical Design (`gf180mcuD`):** `44,345` cells, `945,812 μm²` die area (`56.85%` utilization), `0` Magic DRC, Netgen LVS Clean, `0` antenna violations (`v1.0.0` GDSII).
- **Verification:** Cocotb 1.9.2 (`Icarus 12.0` + `Verilator 5.020`) `2/2` PASS in CI (run `44594199310`).
