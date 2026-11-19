---
id: cocotb-apb3-axi-lite-checkers
featured: false
title: Building Passive AMBA APB3 & AXI-Lite Protocol Checkers in Cocotb
excerpt: Designing non-intrusive bus snoopers that validate IDLE -> SETUP -> ACCESS handshakes and zero-wait slave responses across automated II regressions.
category: IP Verification
date: Oct 30, 2026
readTime: 7 min read
---

Passive protocol monitors decouple bus compliance assertions from testbench stimulus, allowing the exact same checker to run during block-level tests and full-chip integration.

### Bus Snooping Pattern
```python
@cocotb.coroutine
async def monitor_apb(dut):
    while True:
        await RisingEdge(dut.pclk)
        if dut.psel.value and dut.penable.value:
            assert dut.pready.value in (0, 1), "Unknown PREADY state during ACCESS"
```
