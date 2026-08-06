# DBMS and SQL for Infrastructure Engineers

[← Platform engineering](../09-platform-engineering/02-gitops-golden-paths.md) · [Next: Pipelines/lakehouse →](02-data-pipelines-and-lakehouse.md)

## Why operations engineers need database fundamentals

Databases own critical state. Infrastructure can be green while queries block, connections exhaust, replication lags, or data becomes inconsistent.

## Relational model

- table/relation contains rows/tuples described by columns/attributes;
- primary key identifies a row;
- foreign key enforces references where configured;
- unique/check/not-null constraints protect invariants;
- index accelerates selected access at write/storage cost;
- schema migration changes data contract.

Normalization reduces update anomalies; denormalization can improve specific reads but increases consistency work.

## Transactions and ACID

- atomicity: transaction commits entirely or not;
- consistency: constraints/invariants move between valid states (application design still matters);
- isolation: concurrent transactions have defined visibility/anomaly behavior;
- durability: committed data survives failures within system guarantees.

Isolation levels trade concurrency/performance against anomalies. Locks, MVCC, deadlocks, and long transactions affect operations.

## SQL you must understand

```sql
SELECT o.id, c.name, o.created_at
FROM orders AS o
JOIN customers AS c ON c.id = o.customer_id
WHERE o.created_at >= CURRENT_DATE - INTERVAL '7 days'
ORDER BY o.created_at DESC
LIMIT 100;
```

Know `SELECT`, filters, joins, grouping/aggregation, sorting/limits, inserts/updates/deletes, transactions, indexes, and explain plans. Never run an unbounded modification without confirming predicate, transaction/backup, and target environment.

## Operational signals

- connection count/pool saturation;
- query latency and slow/top queries;
- lock waits/deadlocks and long transactions;
- CPU, memory/cache, disk capacity, IOPS/latency;
- replication lag and replica health;
- checkpoint/WAL/log growth;
- backup age/success and restore duration;
- schema/version compatibility.

## Connection management

Every app instance opening too many connections can overwhelm the DB after autoscaling. Use bounded pools, timeouts, backoff/jitter, circuit breaking, and capacity budgets. A DB connection is stateful and expensive compared with a stateless HTTP request.

## Backups and HA

Replication is not backup: a bad delete can replicate. Backups are not HA: restoration takes time. Use replication/failover for availability and independent backups/PITR for recovery; test both.

## Interview proof

Explain an index trade-off, inner versus left join, transaction isolation, connection exhaustion, replication versus backup, and a safe schema rollout.

