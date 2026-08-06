# Twelve-Week Fundamentals and Interview Plan

[← Interview index](README.md)

Use 60–90 minutes on weekdays and one 2–3 hour weekend lab. If an interview is sooner, combine adjacent weeks but keep dependency order.

| Week | Focus | Proof |
|---:|---|---|
| 1 | OS/kernel, processes, boot, files | explain boot; diagnose process/file-descriptor issue |
| 2 | Linux identity, systemd, logs, packages | secure systemd service with runbook |
| 3 | Networking, DNS, HTTP, TLS, SSH/firewall | trace and troubleshoot one HTTPS request |
| 4 | Storage/LVM/NFS, performance, backup | disk incident lab + tested restore |
| 5 | Git, shell, APIs/data formats | safe automation with dry-run/JSON output |
| 6 | Container internals, Dockerfile, Compose | non-root multi-stage image + health/volume/network |
| 7 | IaC/OpenTofu and Ansible | remote-state design + idempotent configuration lab |
| 8 | CI/CD, tests, OIDC, releases | build-once pipeline and canary/rollback explanation |
| 9 | Cloud IAM/VPC/compute/storage/DB/cost | draw two-AZ service and threat/cost review |
| 10 | Kubernetes API/workloads/network/storage/security | deploy and break/fix five scenarios |
| 11 | OTel, SLO, incidents, capacity | dashboard + SLO + postmortem |
| 12 | chosen role + project stories + mock interviews | 40 scenarios, six stories, two system designs |

## Weekly rhythm

- Day 1: read and make one Feynman card.
- Day 2: build minimal system.
- Day 3: break it safely and collect evidence.
- Day 4: answer scenario questions aloud.
- Day 5: revise diagram/runbook.
- Weekend: integrate into project and record proof.

## Role adjustments

- DevOps: spend extra time weeks 7–9 on CI/CD/IaC/cloud.
- SRE: spend extra time weeks 3–4 and 11 on performance/SLO/incidents.
- Platform: spend extra time weeks 8–10 plus platform/GitOps chapters.
- Linux Admin: expand weeks 1–4 and reduce Kubernetes to essentials.

## Application readiness gate

Apply when you can:

- score at least 2 on 30 of 40 scenarios and 3 on 15;
- present one architecture in five minutes;
- tell three evidence-based incident/automation stories;
- explain every must-have in the target JD honestly;
- identify gaps without pretending.

Do not wait for perfect coverage. Apply while improving, but tailor the resume and study plan to each role.

