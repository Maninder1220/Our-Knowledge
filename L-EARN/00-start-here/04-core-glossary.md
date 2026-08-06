# Core Glossary

[← Home](../README.md)

Use this for active recall. Each definition is intentionally short.

| Term | Working definition |
|---|---|
| API | A contract through which software requests operations or data. |
| Artifact | An immutable output of a build, such as an image, binary, or package. |
| Availability | Fraction of valid requests or time in which a service meets its success criteria. |
| CIDR | IP prefix notation containing a network address and prefix length. |
| Control loop | Repeatedly observes actual state and acts toward desired state. |
| Desired state | The condition declared by a user or configuration. |
| DNS | Distributed hierarchical system mapping names to typed records. |
| Error budget | Allowed unreliability implied by an SLO. |
| Idempotent | Repeating an operation converges to the same result. |
| Image | Immutable filesystem layers plus runtime configuration used to create containers. |
| Kernel | Privileged OS core that manages processes, memory, devices, filesystems, and networking. |
| Latency | Time taken for an operation; examine distributions, not only averages. |
| Least privilege | Grant only the access needed, for only as long as needed. |
| Metric | Numeric measurement associated with time and dimensions/attributes. |
| Module | Reusable IaC/configuration boundary with inputs, resources/tasks, and outputs. |
| Namespace | A scope that isolates names or views of system resources. |
| OIDC | Identity protocol used for federated, short-lived authentication. |
| OTLP | OpenTelemetry protocol for transporting telemetry. |
| Process | A running program with virtual memory, threads, file descriptors, credentials, and namespaces. |
| Reconciliation | Comparing actual and desired state, then correcting drift. |
| Reverse proxy | Server that accepts client traffic and forwards it to backend services. |
| Saturation | Queued work caused by demand approaching or exceeding capacity. |
| SLI | Measured indicator of user-relevant service behavior. |
| SLO | Target range for an SLI over a time window. |
| State | Information that must persist for correct future behavior. |
| Telemetry | Signals emitted about system behavior: commonly traces, metrics, and logs. |
| Toil | Manual, repetitive, automatable operational work that scales with service growth. |
| Trace | Causally related spans representing an end-to-end operation. |
| Trust boundary | Point where identity, privilege, network, or ownership assumptions change. |

## Confusing pairs

| Pair | Distinction |
|---|---|
| Authentication / authorization | Who are you? / What may you do? |
| Encryption / hashing / encoding | Reversible with key / one-way digest / representation change |
| Container / VM | Shared host kernel isolation / virtual hardware with guest kernel |
| Monitoring / observability | Known health checks and alerts / ability to investigate system state from outputs |
| CI / continuous delivery / continuous deployment | integrate and validate / keep deployable / deploy automatically |
| Backup / high availability / disaster recovery | recover data / continue through component failure / restore service after major loss |
| Log / metric / trace | discrete event / time-series measurement / request-centric causal path |
| Readiness / liveness / startup probe | receive traffic? / restart needed? / still starting? |
| Secret / ConfigMap | sensitive configuration requiring stronger controls / non-sensitive configuration |
| Service / Ingress / Gateway | stable L4 discovery / limited HTTP entry API / extensible role-oriented traffic API |

