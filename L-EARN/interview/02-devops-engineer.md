# DevOps Engineer Interview Path

[← Role comparison](01-role-comparison.md)

## Role outcome

Improve the flow of changes from source to reliable production using collaboration, automation, infrastructure, and feedback.

## Must study—in this order

1. Linux processes, systemd, permissions, logs, storage, networking.
2. DNS, HTTP/TLS, ports, routing, load balancing.
3. Git branches, PRs, merge/rebase/revert, secret hygiene.
4. Shell plus one stronger language; YAML/JSON and APIs.
5. Docker internals, Dockerfile, networking/storage/security.
6. CI/CD stages, tests, artifacts, OIDC/secrets, release strategies.
7. OpenTofu/Terraform state/modules/plan and Ansible idempotency.
8. One cloud: IAM, VPC, compute/container, storage, DB, monitoring, cost.
9. Kubernetes architecture/workloads/networking/troubleshooting if required.
10. Observability and incident basics.

## Must be able to demonstrate

- a pipeline that builds once and promotes an immutable artifact;
- IaC plan/apply with remote locked state and review;
- a secure containerized service;
- deployment with rollback/verification;
- cloud IAM using a role rather than static keys;
- one incident using logs/metrics/events and root-cause mechanism;
- backup and restoration thinking.

## Deprioritize from your notes

- Deep Trino/Hive/Querybook/Airflow/Ranger details unless the company runs data platforms.
- Kernel source/advanced internals beyond processes, memory, filesystems, networking, namespaces/cgroups.
- Ruby, Go, Rust, and PowerShell all at once; choose shell plus one language relevant to the role.
- Memorizing every Docker/Kubernetes command. Practice scenarios.
- AI agent architecture unless used as a portfolio differentiator after core questions.
- Finance notes and personal interviewer/contact pages.

## Likely questions

1. Design CI/CD for a containerized API.
2. Terraform plan will replace a database—what do you do?
3. Container works locally but not in CI/production—how do you investigate?
4. How do you store and deliver secrets?
5. Explain blue/green versus canary versus rolling.
6. What happens when you enter a URL?
7. `df` is full but `du` is smaller—why?
8. How do you prevent two IaC applies from colliding?

## Strong project choice

Use the [ECS Fargate project](../12-projects/01-ecs-fargate-project.md) for AWS-heavy roles or your Rust/Kubernetes/SigNoz project for Kubernetes roles. Keep the answer around delivery outcomes, reliability, security, and troubleshooting—not tool count.

## Avoid these answer patterns

- “DevOps is a tool/toolchain.” It is a collaborative delivery/operations capability.
- “CI/CD means Jenkins.” Jenkins is one implementation.
- “Terraform supports every cloud with the same code.” Providers/resources differ.
- “We store secrets in GitHub/Jenkins and echo them as env.” Explain scope, OIDC/secret manager, masking limits, and rotation.

