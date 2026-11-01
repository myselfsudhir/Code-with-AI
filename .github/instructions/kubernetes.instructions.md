---
name: Kubernetes and container standards
description: Dockerfiles, Kubernetes manifests, Helm, probes, resources and rollout safety.
applyTo: "**/Dockerfile,**/docker-compose*.yml,**/k8s/**,**/kubernetes/**,**/helm/**,**/*.yaml,**/*.yml"
---
# Kubernetes standards
- Inspect the target Kubernetes version and existing deployment conventions before using API fields.
- Use non-root containers, minimal trusted base images, pinned versions/digests where operationally appropriate and multi-stage builds.
- Never bake secrets into images or manifests; use approved secret management.
- Define CPU/memory requests and limits based on measured or documented needs.
- Configure startup, readiness and liveness probes for distinct purposes; do not use liveness to test downstream dependency availability.
- Handle SIGTERM and graceful shutdown; allow in-flight requests to complete within termination grace periods.
- Use rolling update strategies and disruption budgets where appropriate.
- Apply least-privilege service accounts and RBAC.
- Restrict network access with NetworkPolicies where supported.
- Use ConfigMaps for non-secret configuration and Secrets or external secret systems for credentials.
- Do not run `kubectl apply`, delete, scale or rollout commands against a real cluster without explicit approval.
- Validate manifests with the project's chosen tools and state what was actually validated.
