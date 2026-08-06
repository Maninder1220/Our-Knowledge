# Site Reliability Engineer Interview Path

[← Role comparison](01-role-comparison.md)

## Role outcome

Apply software engineering to operations so services meet explicit reliability objectives with sustainable human effort.

## Must study—in this order

1. Linux performance, networking, processes, storage, failure analysis.
2. Programming/automation, APIs, concurrency, timeouts/retries/idempotency.
3. Distributed-system failure: partial failure, queues, consistency, backpressure.
4. Logs/metrics/traces and OpenTelemetry pipelines.
5. SLI, SLO, error budget, burn-rate alerting.
6. Incident response, on-call, postmortems, toil reduction.
7. Capacity planning, load testing, overload control, graceful degradation.
8. Cloud/Kubernetes reliability, backups, DR, multi-AZ/failure domains.
9. Safe change/release engineering and DORA context.

## Must be able to demonstrate

- define a user-centered SLI/SLO and calculate its error budget;
- design page-worthy burn-rate alerts;
- investigate tail latency and saturation;
- explain retry storms and bounded retry budgets;
- lead an incident timeline and choose mitigation;
- automate repetitive work with safety/verification;
- define RPO/RTO and restoration test;
- explain capacity/headroom under one failure domain loss.

## Deprioritize from your notes

- Long tool installation sequences unless they illustrate an incident.
- Jenkins/GitHub syntax details beyond reliable release design.
- Every AWS service; focus failure modes, identity, capacity, and managed-service behavior.
- Data-lake product details unless the SRE role supports them.
- Platform portal/product depth unless the job combines SRE/platform.
- Command memorization without telemetry/hypothesis reasoning.

## Likely questions

1. Design an SLO for checkout/login/email delivery.
2. A service meets average latency but users complain—why?
3. CPU is low while latency and load average rise—what next?
4. How do you avoid alert fatigue?
5. Describe an incident and your exact evidence.
6. What is toil and what would you automate first?
7. How can retries cause an outage?
8. How do HA, backup, and DR differ?

## Answer lens

Always connect mechanism to user impact and an objective: “The dependency timeout exceeded the edge timeout, causing abandoned work and retry amplification; we aligned deadlines, bounded retries, added a saturation SLI, and load-tested the failure path.”

## Avoid these answer patterns

- “99.9 means 43 minutes every month” without stating event-based versus time-based SLI and window.
- “Observability is logs, metrics, traces.” Those are signals; observability is a system property/capability.
- “Restart fixed it.” That is mitigation unless mechanism/prevention are known.
- “SRE is production support.” It includes engineering, objectives, automation, and reliability trade-offs.

