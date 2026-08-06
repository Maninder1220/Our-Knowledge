# Workloads, Scheduling, Probes, and Resources

[← Architecture](01-architecture-api-lifecycle.md) · [Next: Networking →](03-networking-services-gateway.md)

## Choose the controller by workload semantics

| Object | Use |
|---|---|
| Pod | atomic scheduling/runtime unit; rarely manage standalone in production |
| Deployment | stateless replicated Pods and rolling updates |
| StatefulSet | stable identity/order and per-Pod storage patterns |
| DaemonSet | one/selected Pod per node, such as node agents |
| Job | finite work expected to complete |
| CronJob | scheduled Job creation |

A ReplicaSet maintains count; a Deployment manages ReplicaSets and rollout history.

## Scheduling flow

```mermaid
flowchart LR
    P["Pending Pod"] --> F["Filter feasible nodes"]
    F --> S["Score nodes"]
    S --> B["Bind Pod to node"]
    B --> K["kubelet starts containers"]
```

Key inputs:

- resource requests and allocatable capacity;
- node selectors/affinity;
- Pod affinity/anti-affinity;
- topology spread constraints;
- taints and tolerations;
- volumes/zone constraints;
- priorities and preemption;
- scheduler plugins/policies.

A toleration permits scheduling onto a tainted node; it does not force it. Affinity can be required or preferred. Overly strict rules can leave Pods Pending.

## Requests and limits

- Request is used mainly for scheduling and influences runtime shares/reservations.
- CPU limit is enforced through throttling/quota behavior.
- Memory limit can lead to cgroup OOM; memory is not safely “throttled” like CPU.
- Missing requests makes capacity decisions unreliable; overly high requests waste schedulable capacity.

Quality of Service classes—Guaranteed, Burstable, BestEffort—affect eviction behavior, but do not replace thoughtful sizing.

Measure working set, peaks, CPU throttling, latency, OOMs, and queueing. Tune from workload evidence, not arbitrary percentages.

## Probes

| Probe | Question | Failure effect |
|---|---|---|
| startup | has slow initialization completed? | delays other probes; repeated failure restarts |
| readiness | may this Pod receive traffic? | endpoint becomes unready |
| liveness | is restart the correct recovery? | kubelet restarts container |

Bad liveness probes turn temporary dependency failures into restart storms. Readiness should reflect ability to serve the bounded request path; it should not depend on every optional downstream.

## Rollouts and availability

Deployments use surge and unavailable limits. A safe rollout also needs:

- correct readiness/startup probes;
- graceful termination and `terminationGracePeriodSeconds`;
- application connection draining;
- PodDisruptionBudget for voluntary disruption (not a guarantee against all outages);
- topology spreading and multiple failure domains;
- rollback/forward-fix decision and metrics;
- database/schema compatibility across versions.

## Autoscaling

- HPA adjusts replica count from metrics; choose metrics aligned to load, not only CPU.
- VPA recommends/adjusts requests and may restart Pods depending mode.
- node autoscaling adds/removes capacity based on unschedulable demand and policy.

Autoscaling cannot repair a downstream bottleneck, lock contention, per-instance memory leak, or unbounded retry storm. Define stabilization windows, min/max, and load-test behavior.

## Pod lifecycle clues

Do not confuse Pod phase with container state or readiness. `Running` can still mean unready or repeatedly crashing containers. Inspect conditions, container states, restart counts, events, and controller rollout status.

## Interview proof

Explain Pending versus CrashLoopBackOff, requests versus limits, Deployment versus StatefulSet, three probes, voluntary disruption, scheduling constraints, and why scaling replicas may not fix saturation.

