---
id: rv32i-13-13-precheck-signoff
featured: true
title: Closing 13/13 ChipFoundry Precheck Sign-Off on an RV32I Core in Sky130A
excerpt: Lessons from hardening a full RV32I core through LibreLane/OpenLane, resolving antenna and Magic/KLayout DRC rules, and passing Caravel wrapper integration.
category: Shuttle Precheck
date: Nov 15, 2026
readTime: 9 min read
---

Taking a custom RISC-V core from clean RTL simulation to a certified 13/13 precheck sign-off requires eliminating every discrepancy between macro-level P&R and top-level shuttle wrapper checks.

### 1. Macro vs. Full-Chip KLayout DRC
Run KLayout DRC with macro/precheck flags and `-rd thr=1` to catch off-grid geometry and metal density violations without triggering false seal-ring errors:

```bash
klayout -b -r sky130A_mr.drc -rd input=rv32i_core.gds -rd report=drc.lyrdb -rd thr=1 -rd feol=true -rd beol=true -rd offgrid=true
```

### 2. Multi-Corner Setup & Hold Closure
Close hold slack across fast-fast (`ff`) corners first before tightening setup constraints on slow-slow (`ss`) corners, keeping clock skew budgets realistic for 130nm standard cells.
