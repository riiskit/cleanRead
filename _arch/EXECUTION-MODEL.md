# EXECUTION MODEL
> Filesystem-as-executable execution model for the riiskit stack.
> Status: Stake-in-the-ground. Marked for JIT evolution.

---

## Core Principle
The filesystem IS the execution graph. The route taken IS the audit record.

Each prompt execution instantiates a dynamic BoM-style Manifest/Itinerary through the 00–05 numbered directory layer topology. The layers are not organizational — they are the execution graph itself.

## Layer Map (00–05)
```
00  — Maestro (orchestration entry, trust envelope seeding)
01  — Gate (initial trust classification, protocol pre-classification)
02  — Relay (scope limiter, membrane boundary repositioning)
03  — Entry (post-invitation pipeline processor)
04  — rep_mgr (reputation manager, cross-session behavioral fingerprint)
05  — Surface (external agent interface — Delivery and Receiver modes)
```

## Manifest / Itinerary
Each prompt instantiates a structured record of:
- Agents traversed
- Gates evaluated
- Context state at each handoff
- Handoff sequence

The Manifest IS the audit trail. No separate logging layer required — the traversal record is the log.

## Security surface
Security and auditability surface is at the prompt/inference event level.
promptSnitch validates completed Manifest against expected routing for that prompt class.
driftWatch monitors in-flight behavioral drift during traversal.

## Prior art citation
Van Clief & McDermott, "Interpretable Context Methodology: Folder Structure as Agentic Architecture," arXiv:2603.16021, March 2026.
riiskit delta: trust membrane, silent_handoff, dynamic gates, behavioral fingerprinting.
