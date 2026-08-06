# Project Evidence and Storytelling Template

[← On-prem project](02-onprem-data-platform.md) · [Interview tracks →](../interview/README.md)

Copy this template for every portfolio project.

## One-line outcome

> Built ______ for ______, reducing/improving ______, validated by ______.

## Problem and constraints

- Users/business need:
- Scale/traffic/data:
- Availability/SLO, RPO, RTO:
- Security/compliance:
- Budget/hardware/time:
- Team and your ownership:

## Architecture

Include one Mermaid diagram with users, entry, compute, state, dependencies, telemetry, and trust boundaries. Label ports/protocols only where they clarify design.

## Decisions

| Decision | Alternative rejected | Reason/trade-off |
|---|---|---|
| | | |

## Delivery and operations

- source/review/branch policy;
- CI tests and artifact creation;
- infrastructure/configuration automation;
- deployment and rollback/forward-fix;
- identity and secrets;
- logs, metrics, traces, dashboards, alerts, SLO;
- backups and restore test;
- cost/capacity.

## One incident

| Field | Evidence |
|---|---|
| Symptom and impact | |
| Timeline/recent change | |
| Hypotheses and tests | |
| Root-cause mechanism | |
| Mitigation/fix | |
| Verification | |
| Prevention | |

## Proof artifacts

- architecture diagram and README;
- source/IaC/playbooks/manifests;
- CI run and test report;
- dashboard/SLO screenshot with sanitized data;
- incident/postmortem;
- restore/game-day result;
- cost estimate and security review.

## Two-minute interview answer

1. 20 seconds: problem and your responsibility.
2. 30 seconds: architecture and request/data flow.
3. 30 seconds: hardest decision and trade-off.
4. 30 seconds: incident and evidence-based fix.
5. 10 seconds: measurable outcome and next improvement.

Never claim production scale, savings, uptime, or team ownership you cannot prove. Depth and honest trade-offs are stronger than inflated tool lists.

