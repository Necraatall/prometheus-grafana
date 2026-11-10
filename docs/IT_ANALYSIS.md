# IT Analysis — Observability Portfolio

Status: **DESIGN / NOT IMPLEMENTED** (2026-11-10). This assessment describes the `master` snapshot; no runtime test was executed.

## Current system

- `compose.yaml`: six services — Prometheus, Grafana, Node Exporter, Elasticsearch, Logstash, Kibana.
- `prometheus/prometheus.yml`: Prometheus self-scrape and Node Exporter scrape at 15 seconds.
- `grafana/datasource.yml`: provisioned Prometheus datasource.
- `logstash.conf`: JSON over TCP on port 5000 into Elasticsearch.
- `README.md` covers only Prometheus/Grafana; `README_RUN_IT.md` attempts to cover all six and includes outdated instructions and placeholder clone URL.
- No version-pinned images, committed Grafana dashboards, automated smoke tests, Kubernetes manifests, Helm chart, or release evidence are currently present.

## Risks and gaps

| ID | Finding | Risk | Proposed response |
|---|---|---|---|
| R01 | Grafana admin password `grafana` hardcoded in Compose | High | Local-only credentials from untracked environment; no shared demo secrets |
| R02 | Unrestricted host-bound ports (3000, 9090, 9100, 9200, 9300, 5000, 5601, 9600) | High | Bind only loopback for local use, restrict ingress in K8s |
| R03 | Elasticsearch/Logstash/Kibana images at 7.10.1 | High | Plan a compatible supported stack after security review, not a blind upgrade |
| R04 | Floating images without digest/version strategy | Medium | Pin and document image provenance |
| R05 | No runnable automated deployment proof | High | CI static checks and Kubernetes smoke tests with real evidence |
| R06 | ELK consumes significant resources | Medium | Opt-in profile, memory/request limits, document requirements |
| R07 | README and Compose disagree | Medium | Replace with verified instructions and explicit NOT_RUN labels |
| R08 | No declared data retention/volume cleanup policy | Medium | Bounded local persistence and explicit safe teardown |

## Functional requirements

1. Developer can run basic monitoring with Docker Compose as fallback.
2. Local Kubernetes is the primary target: k3d/K3s + Helm; no paid cloud required.
3. Prometheus scrapes demo workload metrics and host exporter metrics.
4. Grafana datasource and dashboards are committed as code.
5. Alert rules and an end-to-end smoke test have evidence.
6. Logging stack remains an optional and independently testable component.
7. CI cannot claim success if required validation was skipped or deployment failed.
8. Every run records source SHA, tool versions, commands and outcomes.
9. Cloud deployment is **future-only**: optional Google Cloud **Always Free Tier** feasibility study, no use of $300 Free Trial credits, no GKE assumption, no automatic provision of paid resources.

## Out of scope for documentation release

No runtime configuration changes, no cluster, no GCP project/account operations, no actual Helm deployment, no claim of production readiness. See [release plan](RELEASE_PLAN.md).
