# Changelog

## 1.0.2
- **Reformat Code** (Ctrl+Alt+L) in `.promql` files formats every expression like `promtool promql format`. Comments and
  blank lines between expressions stay; expressions with syntax errors or comments inside are left alone.
- New intention **Format all expressions in this file** (Alt+Enter inside any `expr:` of a rule file): formats every
  expression in one step. Checked on 180 rule files (kube-prometheus, Thanos, Prometheus, awesome-prometheus-alerts):
  identical to formatting each expression on its own, YAML still loads, and the Prometheus parser sees the same queries.
- Fix: *Format expression* is no longer offered when a YAML `expr:` block also holds `#` comment lines, which it would
  have dropped.

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
