# Release Plan and Backlog

All entries below are **planned**. Documentation exists but runtime behavior is not yet verified. Issue IDs are stable links to the GitHub backlog.

| Release | Issue | Scope | Acceptance | State |
|---|---|---|---|---|
| v0.1 | OBS-001 | Security baseline for Compose: loopback binding, non-committed passwords, explicit pins | Static config proof + local smoke test | TODO |
| v0.1 | OBS-002 | Baseline reproducible execution and corrected README | Six-service inventory, startup/teardown output, actual status recorded | TODO |
| v0.2 | OBS-003 | K3d/K3s + Helm minimal Kubernetes deployment | Helm lint, deployment rollout and teardown work locally | TODO |
| v0.2 | OBS-004 | Monitoring demo workload and targets | FastAPI `/metrics`; scrape targets up and recorded | TODO |
| v0.3 | OBS-005 | Grafana dashboard provisioning and alerts | Dashboard as code; rule evaluation demonstrably works | TODO |
| v0.3 | OBS-006 | Kubernetes hardening: limits, probes, volumes, secrets, ingress | Validated manifest/security policy; no committed credentials | TODO |
| v0.4 | OBS-007 | CI quality/security gate | Workflows fail closed on incomplete validations and publish evidence | TODO |
| v0.4 | OBS-008 | Real end-to-end smoke and reproducibility checks | Exact SHA, cluster bringup/teardown, assertions, logs | TODO |
| v0.5 | OBS-009 | Optional ELK upgrade, isolated resources and logging integration | Supported compatible versions and sample ingest query | TODO |
| v1.0 | OBS-010 | Google Cloud Always Free feasibility and optional manual demonstration | Pricing and quota review, no $300 trial; prove no unwanted deployment/spend, otherwise NO_GO | TODO |

## Release conditions

Refer to [RELEASE_GATE.md](RELEASE_GATE.md). Do not claim a passing runtime test or production readiness based on documentation-only PRs.

## Next step

Complete OBS-001 / OBS-002 before implementing Kubernetes; do not turn on cloud resources as part of regular CI.
