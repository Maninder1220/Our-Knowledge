# Platform Engineer Interview Path

[← Role comparison](01-role-comparison.md)

## Role outcome

Build and operate an internal platform as a product that lets application teams deliver safely with less cognitive load.

## Must study—in this order

1. Strong Linux/networking/container/Kubernetes foundations.
2. IaC modules/state/policy and cloud account/network/identity design.
3. CI/CD reusable workflows, artifacts, supply-chain security.
4. GitOps reconciliation, desired-state repositories, drift/emergency changes.
5. Kubernetes multi-tenancy, RBAC, NetworkPolicy, quotas, admission, storage.
6. Golden paths, templates, service catalog/metadata, self-service APIs.
7. Platform-as-product: personas, feedback, adoption, SLO, deprecation.
8. Observability and operations for platform and tenant workloads.
9. Cost visibility and governance.

## Must be able to demonstrate

- design a golden path from “new service” to production;
- choose platform boundaries and tenant isolation;
- provide least-privilege workload identity and secret delivery;
- explain GitOps pull/reconciliation and CI relationship;
- version and upgrade templates/modules without trapping users;
- define platform SLO/support/deprecation;
- measure developer outcome, not number of resources;
- support escape hatches with governed exceptions.

## Deprioritize from your notes

- Deep host command lists once Linux fundamentals are proven.
- Data-lake components unless building a data platform.
- Tool-specific Jenkins internals if the role standardizes elsewhere; know reusable pipeline concepts.
- Full packet-analysis/security-tool depth unless networking is central.
- AI agents until the basic platform product, APIs, tenancy, policy, and operations are clear.
- One-off shell installers that do not expose stable platform contracts.

## Likely questions

1. What is an internal developer platform and who are its users?
2. Design self-service provisioning for a database.
3. How do you prevent a golden path from becoming a golden cage?
4. GitOps versus pipeline push deployment?
5. How do you isolate Kubernetes teams?
6. How do you roll out a breaking template/module change?
7. Which platform metrics matter?
8. How do policy exceptions work?

## Avoid these answer patterns

- “A platform is Backstage/Argo/Kubernetes.” Tools are implementation choices.
- “Self-service means giving developers cluster-admin/cloud-admin.” Provide scoped capabilities.
- “Golden path is mandatory for everything.” State defaults, value, supported boundaries, and escape hatch.
- “GitOps is YAML in Git.” Include automatic pull and continuous reconciliation.

