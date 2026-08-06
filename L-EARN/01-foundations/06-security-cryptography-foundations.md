# Security and Cryptography Foundations

[← APIs/proxies](05-apis-proxies-load-balancers.md) · [Linux administration →](../02-linux-administration/01-users-permissions-sudo.md)

## Security begins with assets and threat model

Ask:

1. What assets/data/actions matter?
2. Who are legitimate users/services/admins?
3. Which trust boundaries and entry points exist?
4. What can an attacker or accident do?
5. Which preventive, detective, and recovery controls reduce risk?
6. How is control effectiveness tested?

## Do not confuse operations

| Operation | Reversible? | Purpose |
|---|---|---|
| encoding | yes, no secret | represent data (base64, UTF-8) |
| encryption | yes, with key | confidentiality |
| hashing | designed one-way | integrity fingerprint; passwords need specialized slow KDF |
| MAC/HMAC | verified with shared secret | integrity + authenticity for parties sharing key |
| digital signature | verified with public key | integrity + signer authenticity/non-repudiation context |

Base64-encoded Kubernetes Secrets are not encrypted merely because they look unreadable.

## Symmetric and asymmetric cryptography

- Symmetric encryption uses shared secret keys and is efficient for bulk data.
- Asymmetric cryptography uses public/private key pairs for signatures, key agreement, and encryption patterns.
- Hybrid protocols such as TLS authenticate with certificates/signatures and derive symmetric session keys for data.

Algorithms are only part of security. Key generation, storage, distribution, rotation, revocation, permissions, nonce/IV use, and backup/recovery often determine real safety.

## Passwords

Store password verifiers using a modern password hashing/KDF with unique salt and tuned work factor (for example Argon2id/bcrypt/scrypt/PBKDF2 according to platform guidance), not general fast hashes such as SHA-256 alone. Use MFA and rate limiting; never log passwords.

## PKI and certificates

A certificate binds a public key to identities/attributes signed by an issuer. Clients validate chain, hostname/SAN, time, key usage/policy, and protocol. Private keys require tight access and rotation. Automate renewal and alert well before expiry; also test reload of the renewed certificate.

## Least privilege and defense in depth

Combine:

- strong federated identity and MFA;
- scoped authorization/roles;
- network segmentation and private defaults;
- workload sandboxing and patching;
- secrets management and short-lived credentials;
- encryption with managed key lifecycle;
- immutable/reviewed changes and supply-chain verification;
- audit/detection and tested response/backups.

No single firewall, scanner, encryption flag, or container makes a system secure.

## Common security mistakes in infrastructure notes

- real credentials in CSV, Markdown, Git, shell history, screenshots, or state;
- `chmod 777`, disabled SELinux, broad security groups as a fix;
- downloading/executing unverified installers as root;
- long-lived cloud keys in CI;
- trusting headers/log/tool output as instructions;
- public management ports and default passwords;
- backups deletable by the same compromised identity;
- vulnerability scan with no patch/exception/ownership process.

## Incident response for exposed secret

Contain and rotate/revoke first. Determine scope/use via audit logs, remove the secret from all current systems/history/artifacts, fix the delivery mechanism, and monitor. Merely deleting the file does not invalidate a copied credential.

## Interview proof

Explain encoding versus encryption versus hashing, TLS certificate validation, least privilege, short-lived identity, secret rotation, and why “encrypted at rest” does not control who can decrypt.

