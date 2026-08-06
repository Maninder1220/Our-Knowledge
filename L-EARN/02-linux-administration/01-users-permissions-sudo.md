# Linux Identity, Permissions, and `sudo`

[← Foundations](../01-foundations/04-scripting-and-data-formats.md) · [Next: systemd →](02-processes-systemd-logs.md)

## Identity model

Linux permission checks use numeric user IDs (UIDs), group IDs (GIDs), supplementary groups, capabilities, ACLs, and security modules such as SELinux/AppArmor. Names are human-friendly mappings; files store numeric ownership.

```bash
id
getent passwd <user>
getent group <group>
namei -l /path/to/file
getfacl /path/to/file
```

This explains a common container/NFS failure: a username can look correct inside one system while the numeric UID owning the mounted directory differs.

## File permissions

`rwx` applies separately to owner, group, and other.

| Permission | File | Directory |
|---|---|---|
| read | read contents | list names |
| write | modify contents | create/delete/rename entries, subject to parent rules |
| execute | execute as a program | traverse/search the directory |

Numeric permissions add read `4`, write `2`, execute `1`. `0750` means owner `rwx`, group `r-x`, others none.

Special bits:

- setuid/setgid on executables can change effective identity;
- setgid on a directory makes new entries inherit its group;
- sticky bit on a shared directory restricts deletion/rename to appropriate owners (for example `/tmp`).

Prefer the least access that makes the service work. Do not “fix” permission errors with recursive `chmod 777`.

## `sudo`, `su`, and login shells

| Command | Meaning |
|---|---|
| `sudo command` | run one authorized command as another user, usually root |
| `sudo -u svc command` | run one command as service user `svc` |
| `sudo -iu svc` | login-style shell as `svc`, using its home/environment |
| `su - svc` | switch to a login shell, typically authenticating as target/root depending policy |

`sudo -iu` is convenient and can be good practice when authorized because it uses the target account's login environment and gives an audit trail. It should not replace least-privilege command rules. Broad `NOPASSWD: ALL` trades convenience for a large escalation path.

Edit policy using `visudo` or a validated drop-in under `/etc/sudoers.d/`. Scope by command, run-as identity, source group, and host where practical.

## Service accounts

A service account should normally have:

- stable UID/GID where shared storage requires it;
- no interactive password;
- no login shell unless operationally required;
- ownership only over its data/config paths;
- read-only configuration and separate writable state;
- systemd sandboxing/capability restrictions;
- rotated, externally managed credentials.

## Authentication versus authorization

Authentication proves identity. Authorization checks permitted actions. SSH keys, passwords, MFA, PAM, and OIDC help authenticate; sudoers, filesystem modes, ACLs, RBAC, and IAM policies authorize.

## Troubleshooting permission denied

1. Identify the exact failing process UID/GIDs: `ps -o user,group,euser,egroup -p <PID>`.
2. Inspect every directory component: `namei -l /path`.
3. Inspect mode, owner, ACL, mount flags, and filesystem type.
4. Check SELinux/AppArmor/audit events; mode bits can be correct while policy denies access.
5. For containers/NFS, compare numeric IDs on both sides and root-squash behavior.
6. Change the smallest correct boundary, then verify as the service user.

## Interview scenarios

- Explain why `sudo -iu app` may work while a systemd service fails.
- Explain `chmod`, `chown`, ACLs, umask, setgid directories, and SELinux as separate layers.
- Design access for a deployment user that may restart one service but not gain a root shell.

