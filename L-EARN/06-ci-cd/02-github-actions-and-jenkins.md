# GitHub Actions and Jenkins

[← Delivery fundamentals](01-delivery-fundamentals.md) · [Next: Testing/releases →](03-testing-release-supply-chain.md)

## Same pipeline model, different control planes

| Concern | GitHub Actions | Jenkins |
|---|---|---|
| pipeline as code | workflow YAML in repository | `Jenkinsfile`, usually Declarative Pipeline |
| execution | hosted or self-hosted runners | controller schedules agents |
| reuse | reusable workflows/composite actions | Shared Libraries |
| identity/secrets | repository/environment/org controls, OIDC | Credentials store/plugins/agent identity |
| governance | permissions, environments, required workflows/checks | RBAC, folders, plugins, shared libraries |
| operations | SaaS control plane unless self-hosted runners | controller/agent/plugin lifecycle is yours |

## GitHub Actions essentials

- triggers (`push`, `pull_request`, manual, schedule, reusable calls);
- jobs, steps, runners, matrices, dependencies, outputs;
- `permissions` for the automatic token—set least privilege;
- environments for deployment protection and environment-scoped secrets;
- concurrency groups to prevent overlapping deploys;
- artifacts versus dependency caches;
- OIDC federation to cloud providers, avoiding long-lived keys;
- pin third-party actions to trusted immutable commits according to policy.

Security boundary: PR code is untrusted. Avoid designs where unreviewed code runs with write tokens, production secrets, or privileged self-hosted runner access.

## Jenkins essentials

- controller stores job/config state and schedules work; agents execute builds;
- use Pipeline as Code in a `Jenkinsfile`;
- prefer Declarative Pipeline for consistent structure and policy;
- Shared Libraries reduce duplication but are trusted code and require version/review controls;
- Credentials are referenced by IDs and scoped, not hardcoded;
- isolate agents, use ephemeral agents where feasible, patch plugins/controller, back up `JENKINS_HOME`, and test restore.

```groovy
pipeline {
  agent any
  options { timeout(time: 30, unit: 'MINUTES') }
  stages {
    stage('Test') {
      steps { sh 'make test' }
    }
    stage('Build') {
      steps { sh 'make artifact' }
    }
  }
  post { always { junit 'reports/*.xml' } }
}
```

Use credential binding only around the minimum step, prevent shell tracing of secrets, and remember masking is not a complete defense against malicious build code.

## Which to prioritize

For interviews, learn the pipeline concepts first. Then explain one tool deeply and map it to the other. Do not memorize every plugin/action. Know runners/agents, credentials, artifacts, caching, concurrency, approvals, reuse, and troubleshooting.

## Troubleshooting

1. Was the workflow triggered and filtered as expected?
2. Was a runner/agent available with required labels/tools/network?
3. Which exact step and exit code failed?
4. Is it source/test failure, credential/permission, dependency/registry, cache corruption, quota, or timeout?
5. Are logs redacted and artifacts available?
6. Can it reproduce in a clean local/container environment?

Sources: [GitHub Actions](https://docs.github.com/actions), [GitHub Actions OIDC](https://docs.github.com/actions/security-for-github-actions/security-hardening-your-deployments/configuring-openid-connect-in-cloud-providers), [Jenkins Pipeline as Code](https://www.jenkins.io/doc/book/pipeline/pipeline-as-code/), [Jenkins Shared Libraries](https://www.jenkins.io/doc/book/pipeline/shared-libraries/).

