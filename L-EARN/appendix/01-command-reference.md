# Command Reference by Question

[← Home](../README.md)

Commands are evidence tools, not fixes. Confirm target/environment and read help before mutation.

## Linux host

| Question | Commands |
|---|---|
| identity | `id`, `getent passwd`, `getent group` |
| path permissions | `namei -l PATH`, `stat PATH`, `getfacl PATH`, `ls -Z PATH` |
| processes | `ps -eo ...`, `top`, `pidstat`, `/proc/PID/*` |
| listening sockets | `ss -lntup` |
| service state | `systemctl status UNIT`, `systemctl cat UNIT`, `systemctl show UNIT` |
| logs | `journalctl -u UNIT -b`, `journalctl -p warning -b` |
| boot | `journalctl -b`, `systemd-analyze critical-chain` |
| filesystems | `findmnt`, `lsblk -f`, `df -hT`, `df -ih`, `du -xhd1 PATH` |
| deleted-open files | `lsof +L1` |
| LVM | `pvs`, `vgs`, `lvs -a -o +devices` |
| memory/pressure | `free -h`, `vmstat`, `/proc/pressure/*`, kernel/OOM logs |
| disk I/O | `iostat -xz`, `pidstat -d` |
| network | `ip -br a`, `ip route`, `ip route get IP`, `ip neigh` |
| DNS/HTTP/TLS | `dig`, `resolvectl`, `curl -v`, `openssl s_client` |
| SELinux | `getenforce`, `ausearch -m AVC -ts recent`, `ls -Z` |

## Docker/Compose

| Question | Commands |
|---|---|
| inventory | `docker ps -a`, `docker image ls`, `docker volume ls`, `docker network ls` |
| effective state | `docker inspect OBJECT`, `docker compose config` |
| logs/exit | `docker logs --since 10m CONTAINER`, inspect state/exit/OOM |
| resources | `docker stats --no-stream`, `docker system df` |
| image | `docker image inspect IMAGE`, `docker history --no-trunc IMAGE` |
| stack | `docker compose ps`, `docker compose logs SERVICE` |

Broad prune/removal commands are intentionally omitted. Resolve exact owned targets before cleanup.

## Kubernetes

| Question | Commands |
|---|---|
| cluster/pods | `kubectl get nodes`, `kubectl get pods -A -o wide` |
| events | `kubectl get events -A --sort-by=.metadata.creationTimestamp` |
| one Pod | `kubectl describe pod POD -n NS` |
| logs | `kubectl logs POD -n NS --all-containers --since=10m`, `--previous` |
| rollout | `kubectl rollout status deployment/NAME -n NS` |
| service path | `kubectl get svc,endpointslice -n NS` |
| auth | `kubectl auth can-i VERB RESOURCE -n NS` |
| resource use | `kubectl top pod,node` when metrics pipeline exists |
| manifest/diff | `kubectl get TYPE NAME -o yaml`, `kubectl diff -f PATH` (protect secrets) |
| debug | `kubectl debug` or bounded `exec` according to authorization |

## OpenTofu/Terraform

| Question | Commands |
|---|---|
| format/validate | `tofu fmt -check -recursive`, `tofu validate` |
| initialize | `tofu init` |
| preview | `tofu plan -out=FILE`, `tofu show FILE` |
| state inventory | `tofu state list`, `tofu state show ADDRESS` (sensitive) |
| machine output | `tofu show -json FILE` (treat as sensitive) |

Never apply/destroy before reviewing exact backend/workspace/target and recovery impact.

## Ansible

| Question | Commands |
|---|---|
| inventory | `ansible-inventory -i INVENTORY --graph` |
| syntax | `ansible-playbook PLAY.yml --syntax-check` |
| preview | `ansible-playbook PLAY.yml --check --diff` |
| bounded run | `ansible-playbook PLAY.yml --limit HOST` |
| verbose evidence | add `-v` levels cautiously; output may contain sensitive data |

## Git

| Question | Commands |
|---|---|
| current changes | `git status`, `git diff`, `git diff --cached` |
| remote changes | `git fetch --prune`, `git log --oneline --decorate --graph --all` |
| history search | `git log -S'TEXT'`, `git log -- PATH`, `git blame PATH` |
| safe shared undo | `git revert COMMIT` |

## Discovery habit

Use `man command`, `command --help`, official versioned docs, and read-only inspection first. In an interview, remembering the exact flag is less important than explaining the question the command answers.

