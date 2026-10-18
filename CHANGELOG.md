# Changelog

## 1.0.1
- New intention **Format expression (promtool promql format)** (Alt+Enter): rewrites the expression exactly as
  `promtool promql format` / Prometheus' prettifier does: lines over 100 characters are split with two-space
  indentation, and the expression is written in Prometheus' normalized form (`sum(x) by (job)` → `sum by (job) (x)`,
  `[90s]` → `[1m30s]`, sorted label matchers, double-quoted strings). In rule files the `expr:` value is rewritten in
  place: a multi-line result becomes a `|` block scalar, a single-line result keeps its quoting style. Not offered for
  expressions that contain comments, because promtool drops them.

## 1.0.0
First release: PromQL highlighting, Prometheus-compatible error checking with quick fixes, 7 PromQL inspections, rule
file structure checks, completion and quick documentation; PromQL inside rule files, PrometheusRule resources and promtool tests.
