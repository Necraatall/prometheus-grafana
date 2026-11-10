# Security Boundaries and Cost Controls

**Existing risks**: Hardcoded Grafana credential in `compose.yaml`; published host ports for Grafana/Prometheus/exporter and ELK; legacy ELK 7.10.1; unpinned images. These are *findings*, not fixed by this documentation change.

## Required mitigation before demonstrating runtime

1. Keep credentials out of git, inject from an ignored local environment or secrets input; rotate shared/demo credentials.
2. Bind local Compose UI endpoints to `127.0.0.1` by default; never publish sensitive UIs on the open Internet.
3. In K8s use port-forward, internal Services, RBAC-minimal accounts, probes and requests/limits. Review NetworkPolicy support.
4. Pin versions with known compatibility; scan images and dependencies.
5. Enforce resource cleanup on demos and document data deletion.

## Google Cloud cost policy

- **Only Always Free Tier is in scope for planning.** Do not rely on time-limited $300 promotional credits or paid GKE cluster/compute.
- No cloud deployment in this stage. Future cloud plan requires checking actual region, service, SKU, machine/storage quotas and billing terms before any operation.
- Billing account eligibility is necessary; budget alerts are **not** hard spending limits.
- Manual, opt-in provisioning only; no infrastructure provisioning triggered on push or PR.
- If strict zero-charge assurance cannot be established, mark cloud experiment **NO_GO** and demonstrate the full stack locally.
