# ADR-0001: Local Kubernetes as primary environment

Status: **Accepted for the architecture proposal; implementation pending**.

Decision: Develop and demonstrate Kubernetes/Helm on local Ubuntu with k3d (K3s). Keep Docker Compose as a fallback. Do not depend on a cloud Kubernetes subscription. Rationale: reproducible lifecycle tests, clear cloud cost boundary, portable skills. Trade-off: local k3d is not evidence of a production managed K8s service.
