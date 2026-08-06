# Source Coverage Map

[← Home](../README.md)

This map shows how the original Notion-style folders were consolidated. Concepts were preserved; exact duplicates, secrets, personal contact lists, and machine-specific values were excluded.

| Original area | Knowledge retained in |
|---|---|
| `Syllabus/Fundamentals`, `RE`, `V-THEORY`, computer networking | `01-foundations/01–02`, Linux networking chapter |
| OS, Linux architecture, kernel, Linux admin roadmap, commands | `01-foundations/01`, all `02-linux-administration` |
| sudo user, permissions, NFS UID/GID incidents | Linux identity/storage and data-platform lessons |
| DNS revision notes | networking/DNS/TLS chapter |
| Git/VCS | Git and collaboration chapter |
| shell, YAML, Groovy, PowerShell | scripting/data formats; CI tool chapter; optional PowerShell and language direction |
| Docker, Dockerfile, layers, Compose, container security | all `03-containers` |
| Kubernetes basics, request lifecycle, kubeconfig | Kubernetes architecture, workloads, config/security |
| Kubernetes networking diagrams | Kubernetes networking/Services/Gateway chapter |
| kubeadm/control/worker/health/troubleshooting notes | Kubernetes operations chapter |
| Terraform `.tf`, deep dive, ECS/EC2 structures | all `05-iac-configuration`, ECS project |
| Ansible YAML | Ansible chapter |
| CI/CD, Jenkins, pipeline, SonarQube, tests, GitHub workflow | all `06-ci-cd` |
| AWS, NACL, S3/access control, ECR/ECS/Fargate, cost | all `07-cloud`, ECS project |
| observability, monitoring, logs/metrics/traces | all `08-observability-sre` |
| DBMS/MySQL/database fragments | `10-data-systems/01` |
| data pipeline/data lake setup, stack mental models | `10-data-systems/02–03`, on-prem project |
| Trino/MySQL/Hive/Postgres/Querybook | data-system model and runbook lessons |
| Spark, Airflow, Logstash/OpenSearch ingestion | data-pipeline model and runbook lessons |
| Keycloak/Ranger/SSL/Ingress problems | K8s security/networking and runbook lessons |
| NFS disk expansion, Postgres permission incident | Linux storage and runbook lessons |
| Rusting/binary/OSAI/AI notes | `11-rust-automation-ai` |
| API, Nginx, server fragments | API/proxy/load-balancer chapter, networking/HTTP/TLS, service operation |
| cryptography and network-security notes | security/cryptography foundations plus Linux/Kubernetes/container security |
| interview notes and video flow | all `interview`, project evidence template |
| shared “Syllabus (1)” | deduplicated against main syllabus |
| empty placeholder pages | replaced by directional index and chapters |
| finance folder | preserved as a corrected, non-advisory chapter under `13-optional-source-notes` |
| Go, Ruby, Python, and additional language fragments | consolidated into role-directed language guidance under `13-optional-source-notes` |
| credentials CSV | excluded for security |
| personal interviewer list | excluded for privacy and because it is not technical knowledge |

## Images and diagrams

The original screenshots/PNG diagrams were used as conceptual input but not copied. Their important relationships were redrawn as text-based Mermaid diagrams so the archive is searchable, editable, versionable, and free of embedded environment details.

## Content status legend

- **Merged:** repeated notes were combined into one authoritative chapter.
- **Corrected:** inaccurate/outdated mental models are documented in `00-start-here/03-source-audit-and-corrections.md`.
- **Generalized:** environment-specific runbooks became reusable mechanisms and acceptance checks.
- **Deprioritized:** valuable but role-specific topics remain referenced in interview paths rather than dominating fundamentals.
