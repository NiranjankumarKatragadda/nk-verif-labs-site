---
id: 1-debugging-hold-violations-on-fast-corners-in-sky130a
featured: false
title: Debugging Hold Violations on Fast Corners in Sky130A
excerpt: How to fix fast-corner hold violations in OpenROAD/LibreLane without degrading setup slack.
category: RTL-to-GDSII
date: Nov 19, 2026
readTime: 1 min read
---

Fast-fast (`ff`) corners frequently expose short-path hold violations across shift registers and pipeline stages.

### Fixing Hold Slack
Enable `PL_RESIZER_HOLD_SLACK_MARGIN` and `GRT_RESIZER_HOLD_SLACK_MARGIN` in your LibreLane config before running sign-off STA.
