# SUBSTRATE DEFENSE ARCHITECTURE
> Hardware enforcement layer specification for the riiskit membrane fabric.
> Status: Prior art documentation. Stake-in-the-ground.

---

## Core Novelty Claim
Heterogeneous substrate chain where no exploit path crosses a layer boundary, combined with a membrane-to-silicon feedback loop:

```
[Software membrane] → [Behavioral fabric] → [Firmware] → [Reconfigurable logic]
```

Each layer is a distinct enforcement substrate. An exploit that compromises one layer cannot traverse to the next without crossing a trust boundary enforced by a different physical/logical substrate.

## Enforcement Chain

### Layer 1: Software membrane
The riiskit membrane fabric (cleanRead, driftWatch, promptSnitch, intentGuard, chunkHound).
Behavioral enforcement at the prompt/inference event level.

### Layer 2: Firmware enforcement nodes
DENY decisions at severity floor 4–5 trigger forwarding to physical edge devices:
- **ESP32** — low-power edge enforcement, network-level filtering
- **Raspberry Pi 4/5** — higher-compute edge enforcement, pattern analysis

These are not passive logging nodes — they are active enforcement surfaces that can block, redirect, or quarantine traffic independent of the software layer.

### Layer 3: Reconfigurable logic (FPGA)
FPGA extends the membrane's dynamic severity adjustment into silicon via partial bitstream reconfiguration. Upstream behavioral intelligence (rep_mgr signals, drift scores) drives bitstream updates — the enforcement logic itself reconfigures in response to threat intelligence.

This is the membrane-to-silicon feedback loop: software behavioral signals → FPGA bitstream reconfiguration → hardware-level enforcement update.

## Why this matters
Existing vendor guardrail products (Google Model Armor, Azure Prompt Shields, AWS Bedrock Guardrails, F5, Prisma AIRS) operate entirely in software and are designed to protect vendor infrastructure. They have no hardware enforcement layer and no feedback loop to silicon.

The substrate chain means:
- A software exploit cannot reach the firmware layer without physical access
- A firmware compromise cannot reconfigure the FPGA without the membrane's behavioral signal pipeline
- The FPGA enforcement state reflects the current threat intelligence — it is not static

## Prior art status
This architecture documents a novel composition of established hardware components (ESP32, RP4/5, FPGA partial reconfiguration) in a configuration not previously implemented in LLM pre-inference security. The novelty claim is compositional, not primitive-level — consistent with riiskit's broader approach.
