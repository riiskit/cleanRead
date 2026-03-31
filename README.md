# cleanRead

> cleanRead is accountable to the user's thematic envelope, not a vendor content policy.
> The vendor content policy protects the vendor. The thematic envelope protects the user.

---

## What it is
cleanRead is the consumer-facing product of the riiskit security stack — a prompt firewall operating at the pre-send inspection zone between a user and any downstream LLM inference endpoint.

It does not replicate existing vendor guardrail products (Google Model Armor, Azure Prompt Shields, AWS Bedrock Guardrails, F5, Prisma AIRS). Those products protect vendor infrastructure and reputation. cleanRead protects the user.

## Position in the stack
cleanRead sits above the membrane fabric. It is the trust-seeding surface where the user's thematic envelope is established. The initial prompt is a trust-seeding event — it defines the envelope against which all subsequent agent behavior is evaluated.

## Related repos
- `promptSnitch` — BoM path validator
- `driftWatch` — behavioral drift detector
- `intentGuard` — gate contract enforcer
- `chunkHound` — chunk-level inspector
- `injectify` — red-team surface (invitation-only)

## Prior art citation
Van Clief & McDermott, "Interpretable Context Methodology: Folder Structure as Agentic Architecture," arXiv:2603.16021, March 2026.
riiskit delta: trust membrane, silent_handoff, dynamic gates, behavioral fingerprinting.

## Status
Active development. Part of riiskit stack at github.com/riiskit.
