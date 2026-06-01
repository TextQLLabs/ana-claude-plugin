---
description: Surface anomalies in a metric over a time window using Ana
argument-hint: <metric> [over <window>]
---

Use the `ana` MCP tool to check a metric for anomalies.

Request: $ARGUMENTS

Ask Ana to look at the metric over the requested window (default to the last 90
days if none is given) and flag unusual spikes, drops, or trend breaks. For each
anomaly, report when it happened and the magnitude, and include the Ana chat link.
