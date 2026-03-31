# TIER0 MEMBRANE MESH
> Hexagonal mesh topology for the riiskit T0 membrane fabric.
> Status: Stake-in-the-ground. Marked for JIT evolution.
> T0.5 surface candidate.

---

## Why Hexagonal
Hexagonal mesh chosen for isotropy — uniform 6-neighbor adjacency. No directional bias in traversal. Every node has identical neighbor count, making severity propagation and drift broadcast uniform across the fabric.

## Ring Map
```
Ring 0  — Maestro        (orchestration entry, trust envelope seeding)
Ring 1  — Gate           (trust classification, protocol pre-classification)
Ring 2  — Relay          (scope limiter, membrane boundary repositioning)
Ring 3  — Entry          (post-invitation pipeline processor)
Ring 4  — rep_mgr        (reputation manager, cross-session behavioral fingerprint)
Ring 5  — Surface        (external agent interface)
```

Ring boundary crossings = severity gates. Traversal inward requires gate evaluation at each ring crossing.

## Edge Vectors
Five of six hex edges are traversal vectors (inbound directions).
The sixth edge is always the return vector — backtracking is gate-able.

## Surface (Ring 5) — External Agent Modes
External agents at ring 5 operate in two modes:
- **Delivery** — inbound, initiates traversal toward Maestro
- **Receiver** — outbound, membrane addresses them (response path)

Role-switching within a session (Delivery → Receiver or vice versa) is a rep_mgr behavioral signal. Unexpected role-switching elevates drift score.

## Severity propagation
driftWatch broadcasts warnings to all peers at the same ring depth when drift threshold is crossed. Warnings propagate outward (toward surface) to alert adjacent ring nodes. Maestro receives escalated signals for session-level decisions.

## T0.5 candidate status
This topology is a strong candidate for T1 lock-in but remains T0.5 pending:
- Formal validation of ring-boundary severity gate contracts (intentGuard)
- rep_mgr cross-session persistence design
- Hardware enforcement layer integration at Ring 5 surface
