# Release Gate — Evidence Policy

Status as of 2026-11-10: **DOCUMENTATION ONLY; implementation NOT_RUN**.

| Check | Status | Required evidence |
|---|---|---|
| Architecture and scope documented | PASS (documentation) | This PR's reviewed docs |
| Local Compose config validated | NOT_RUN | `docker compose config` plus tool version |
| Six-service runtime smoke test | NOT_RUN | real service logs and health results |
| Helm lint and template validation | NOT_RUN | commands/versions/exit codes |
| Local Kubernetes rollout | NOT_RUN | exact SHA, deployment status, pod health |
| Metrics endpoints and Prometheus targets | NOT_RUN | queries/target state |
| Grafana dashboards and alert rules | NOT_RUN | dashboard queries and evaluated rules |
| Optional ELK ingest | NOT_RUN | sample log ingestion and search evidence |
| Secrets, dependency, image security checks | NOT_RUN | scanner report, exit code, findings |
| CI reproducibility on actual code | NOT_RUN | GitHub Actions run permalink and commit SHA |
| Google Cloud Always Free feasibility | NOT_RUN | independently checked quotas/pricing and safe plan |
| Google Cloud deployment | NOT_RUN / OPTIONAL | manual approval, no paid resources; otherwise NO_GO |

**PASS** requires real evidence, never inferred from an intended configuration. **NOT_RUN** means untested, not passing. No automatic release if a mandatory check is missing. The cloud experiment must not be a requirement to pass the local release gate.
