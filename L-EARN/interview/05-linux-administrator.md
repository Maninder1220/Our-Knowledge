# Linux Administrator Interview Path

[← Role comparison](01-role-comparison.md)

## Role outcome

Keep Linux hosts and core services secure, available, recoverable, and supportable across their lifecycle.

## Must study—in this order

1. Boot process, kernel/user space, processes/threads/signals.
2. Filesystem hierarchy, inodes, mounts, permissions/ACLs, links.
3. Users/groups, sudo, PAM basics, service accounts.
4. systemd units/dependencies, journal, package/repository management.
5. IPv4/IPv6, CIDR, routing, DNS, ports/sockets, SSH, firewalls.
6. Storage: partitions, LVM, XFS/ext4, NFS, capacity/inodes, backup/restore.
7. Performance: CPU/load, memory/swap/OOM, disk latency, network, PSI.
8. Security: patching, least privilege, SELinux/AppArmor, auditing, hardening.
9. Shell automation and configuration management.
10. VM/container basics and monitoring.

## Must be able to demonstrate

- diagnose a failed systemd service;
- recover disk-full/inode/deleted-open-file issues;
- explain numeric ownership and fix a permission/SELinux issue safely;
- troubleshoot SSH timeout versus refused versus auth denied;
- grow an LVM/filesystem only after mapping layers;
- find CPU, memory, I/O, and network bottlenecks;
- define backup RPO/RTO and perform restore;
- patch/reboot with validation and rollback/recovery.

## Deprioritize from your notes

- Deep Kubernetes API/controllers/operators unless the role includes cluster administration.
- Jenkins/GitHub Actions syntax and advanced release strategies.
- Platform-as-product, portals, golden paths, DORA metrics.
- AWS service catalogue beyond the company's environment.
- Trino/Hive/Airflow/Ranger and AI agents unless explicitly supported by the role.
- Ruby/Go/Rust language depth; shell plus Ansible/Python may be more relevant.

## Likely questions

1. Server load is high but CPU is not—why?
2. `df` and `du` disagree—explain.
3. Service works when run manually but fails under systemd.
4. What happens during boot?
5. How do symbolic and hard links differ?
6. How do you troubleshoot DNS and route selection?
7. Permission bits look correct but access is denied.
8. How would you safely extend storage and verify it?

## Avoid these answer patterns

- Running `chmod 777`, disabling SELinux, or opening the firewall as a permanent fix.
- Restarting before collecting evidence when impact allows investigation.
- Saying “Linux uses free RAM badly”; explain page cache and reclaim.
- Treating every high load as CPU saturation.

