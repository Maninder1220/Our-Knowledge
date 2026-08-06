# Hands-On Lab Path

[← Home](../README.md)

Use disposable VMs/accounts/namespaces. Never run failure labs against production or data you cannot restore.

| Lab | Build | Break safely | Evidence/proof |
|---:|---|---|---|
| 1 | systemd service as non-root user | wrong config path/permission | journal, exit code, `namei`, fixed unit |
| 2 | HTTPS service behind Nginx | wrong upstream port / hostname | 502/TLS evidence and request flow diagram |
| 3 | small subnet/routing lab | wrong route/firewall | `ip route get`, socket, packet path |
| 4 | filesystem/LVM test disk | fill blocks/inodes; hold deleted file | `df`/`du`/`lsof`; safe recovery |
| 5 | multi-stage non-root container | bind only localhost/wrong volume UID | inspect, logs, network/ownership fix |
| 6 | Compose API + DB | use `localhost`, start DB slowly | DNS/service name, retry/readiness behavior |
| 7 | OpenTofu disposable network/VM | introduce drift / plan replacement | reviewed plan, move/import choice, state design |
| 8 | Ansible role | non-idempotent command | second run `changed=0`, handler/validation |
| 9 | CI pipeline with OIDC design | failing test/untrusted PR | permissions and artifact trust explanation |
| 10 | Kubernetes Deployment/Service | selector, probe, limit, PVC failures | five incident cards |
| 11 | OTel-instrumented API | collector exporter unavailable | app survives, queue/drop telemetry visible |
| 12 | SLO/game day | dependency delay/5xx injection | burn alert, mitigation, postmortem, follow-up |

## Lab report template

```markdown
# Lab: name

## Goal and safety boundary
## Architecture and versions
## Expected behavior
## Failure injected
## Evidence collected
## Root-cause mechanism
## Fix and user-level verification
## Prevention/automation
## Three interview questions
```

## Graduation project

Combine labs into one service:

- Git + CI builds one signed/digested image;
- OpenTofu creates cloud infrastructure;
- Ansible configures a host or Kubernetes deploys the workload;
- DNS/TLS/proxy expose it;
- database/object state is backed up and restored;
- OpenTelemetry sends logs/metrics/traces;
- an SLO and burn-rate alert represent the user journey;
- a documented game day proves recovery.

This one connected project is more valuable than twelve isolated tool demos.

