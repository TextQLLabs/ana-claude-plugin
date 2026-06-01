---
description: Break a KPI down across a dimension over a time period using Ana
argument-hint: <metric> by <dimension> [over <period>]
---

Use the `ana` MCP tool to break down a KPI across a dimension.

Request: $ARGUMENTS

Ask Ana to compute the metric, segmented by the requested dimension, over the
requested time period (default to the last full month if none is given). Return
the breakdown as a ranked table (highest to lowest), call out the top and bottom
segments, and include the Ana chat link so the user can drill in further.
