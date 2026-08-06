# Scenario Question Bank

[← Interview index](README.md)

Answer aloud before reading notes. Use scope → evidence → hypothesis → safe action → verification → prevention.

## Linux and networking

1. A service is active but port 8080 is unreachable remotely. Walk the path.
2. `df -h` is 100%, but deleting visible logs changes nothing.
3. Load average is 30, CPU is 20%. What does that suggest?
4. A systemd service fails only after reboot but works manually.
5. SSH returns timeout for one host, refused for another, permission denied for a third.
6. Files are mode `0770`, yet the container cannot write to NFS.
7. DNS resolves differently inside a Pod than on the node.
8. TLS certificate is valid but the client reports hostname mismatch.

## Containers and Kubernetes

9. Container exits instantly with code 0.
10. App connects to DB on localhost locally but fails in Compose.
11. Pod is Running but gets no Service traffic.
12. Deployment rollout is stuck at one unavailable replica.
13. Pod is Pending after adding a PVC.
14. Application is OOMKilled even though node memory looks free.
15. NetworkPolicy default deny breaks telemetry and DNS.
16. `ImagePullBackOff` begins after a release.

## IaC and CI/CD

17. Plan proposes replacing a production database.
18. Two engineers need to apply the same state.
19. A resource was manually changed in the console.
20. CI from a fork requests cloud credentials.
21. Build passes only after retrying tests three times.
22. Rollback fails after a schema migration.
23. Same image tag produces different behavior across environments.
24. Ansible reports changed on every run.

## Cloud and reliability

25. One AZ fails; what continues and what does not?
26. NAT cost suddenly rises.
27. Autoscaling adds application instances but latency worsens.
28. RDS connections are exhausted after scaling tasks.
29. Backups show success; how do you know recovery works?
30. 5xx is low, but SLO burn is high—how?
31. An alert pages every night without user impact.
32. A dependency timeout causes retry amplification.

## Platform and design

33. Design a golden path for a new API.
34. Developers bypass the platform because it is slow.
35. A GitOps hotfix is automatically reverted.
36. A template update must reach 100 repositories.
37. Teams need Kubernetes isolation but share one cluster.
38. Policy blocks a legitimate exceptional workload.
39. Choose ECS Fargate versus EKS.
40. Define metrics for platform success.

## Self-scoring

Score each 0–3:

- 0: no coherent answer;
- 1: definitions/commands only;
- 2: mechanism and evidence, incomplete safety/verification;
- 3: scoped mechanism, evidence, trade-off, safe mitigation, verification, prevention.

