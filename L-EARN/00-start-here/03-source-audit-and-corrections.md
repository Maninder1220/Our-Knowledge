# Source Audit, Gaps, and Corrections

[← Home](../README.md)

## What was found

The uploaded nested export contained:

| Item | Count / observation |
|---|---|
| Markdown notes | 231 files, roughly 174,000 words |
| Images | 23 PNG diagrams/screenshots |
| Other | 1 PDF and 1 credentials CSV |
| Duplication | 72 duplicate Markdown instances, mainly the “Sharing is Caring” copy |
| Strongest clusters | Linux, Docker, Kubernetes networking/API, troubleshooting, data-platform deployment |
| Weakest clusters | coherent order, SRE practice, platform-as-product, GitOps, state/security discipline, backup/DR, measurable outcomes |

## Strengths worth keeping

- You think in flows: DNS → connection → application and Kubernetes API → controller → workload.
- You record real failures, especially permissions, NFS, database, ingress, certificates, and deployment errors.
- You connect Linux kernel concepts—processes, namespaces, cgroups, filesystems—to containers.
- You have moved beyond definitions into architecture, ports, storage, and multi-service systems.
- Your Kubernetes request-lifecycle and troubleshooting notes are stronger than typical entry-level notes.

## Important corrections

| Earlier note | Correct mental model |
|---|---|
| DNS means “Domain Naming Service” or translates IP to name | DNS is the **Domain Name System**. Normal forward lookup maps a name to records; reverse DNS maps an IP to a PTR name. |
| A resolver is the ISP | A client may use an OS stub, router, enterprise resolver, ISP resolver, or public resolver. |
| HTTP relies on TCP | HTTP/1.1 and HTTP/2 normally use TCP; HTTP/3 uses QUIC over UDP. |
| IP address is always a unique device ID | An IP identifies an interface/location in a routing scope. NAT, private ranges, DHCP, anycast, and multiple interfaces break the “one global unique device” model. |
| Public and private are types inherent to subnets | In cloud systems, a subnet is effectively public when its routing and gateway path allow public reachability; the CIDR alone does not make it public. |
| Metrics and traces are built on logs | Logs, metrics, and traces are distinct telemetry signals. They can be correlated, but none must be derived from another. |
| Terraform is one codebase for four clouds | The language/workflow is shared, but resources and behavior are provider-specific. Multi-cloud still needs provider-specific design. |
| Every `.tf` file is a module | All `.tf` files in one directory are evaluated together as one module. A directory is the module boundary. |
| Provisioners are a normal configuration pattern | Provisioners are a last resort. Prefer images, cloud-init, configuration management, or native provider resources. |
| Docker image is an OS | An image is an immutable filesystem/config bundle. It normally shares the host kernel; it is not a full guest OS. |
| Stopping a container loses its writable data | Stopping preserves the writable layer; removing the container normally removes it. Volumes are the correct place for durable data. |
| Kubernetes workers run Docker | Kubernetes uses a CRI-compatible runtime. Direct dockershim integration was removed in Kubernetes 1.24. Common runtimes include containerd and CRI-O. |
| Kubernetes gives disaster recovery out of the box | Controllers provide reconciliation and replacement, not a complete DR plan. You still need backups, restore tests, multi-zone design, data replication, and runbooks. |
| kube-proxy IPVS is a best choice | In Kubernetes 1.36, nftables mode is stable and IPVS mode is deprecated. Check CNI/runtime compatibility before migration. |
| Ingress is the future entry API | Gateway API is the successor and provides richer, role-oriented routing. Ingress remains supported but is limited/frozen. |

## Missing knowledge added here

- Boot chain, systemd dependency behavior, package/repository trust, SELinux/AppArmor basics.
- Linux performance method: utilization, saturation, errors, PSI, OOM, I/O latency.
- IPv6, NAT, routing tables, stateful firewalls, TLS/PKI, load balancing, proxies.
- Git conflict/rebase/revert thinking and protected collaboration workflows.
- OpenTofu state encryption, locking, drift, imports/moves, testing, and blast radius.
- CI identity using OIDC, immutable artifacts, provenance, security gates, and release strategies.
- Kubernetes resources/limits, probes, disruption budgets, autoscaling, admission, RBAC, NetworkPolicy, backup/restore.
- OpenTelemetry Collector pipelines, semantic context, cardinality, retention, sampling, and cost.
- SLI/SLO/error budgets, burn-rate alerts, incident command, postmortems, capacity and toil.
- Platform-as-product, golden paths, GitOps reconciliation, multi-tenancy, and developer experience.
- Role-specific “must know” versus “deprioritize” guidance.

## Material deliberately excluded

- The credentials CSV and any literal secrets or tokens.
- Personal recruiter/interviewer contact lists.
- Exact duplicates.
- Machine-specific IP addresses and environment-specific credentials; incident mechanisms were preserved using safe placeholders.

Finance, PowerShell, and extra programming-language notes were retained under `13-optional-source-notes`. They are separated from the core infrastructure sequence because their relevance depends on personal goals or the target environment.

## Freshness warnings

The following topics age quickly: Kubernetes versions/APIs, cloud pricing, CI action versions, container runtime support, Linux distribution commands, OpenTofu/Terraform features, and security guidance. Use [the reference index](../appendix/03-official-references.md) before production work.
