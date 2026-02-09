# Project State / Overlay

## Contract Inheritance
This project **inherits and is governed by**:

- `pcb-design-contract.md`

All rules, invariants, and validation requirements in the base contract apply unless explicitly overridden here.

---

## Project Identification
- **Project name:**
- **Repository path:**
- **Current revision:**
- **Status:** (e.g. concept / schematic / layout / prototype / verified)

---

## Intent & Scope
**Purpose of this PCB:**

- (Describe what the board does, not how it is implemented.)

**Out of scope:**

- (Explicitly state what this board is not intended to do.)

---

## External Interfaces
**Power rails:**
- (e.g. +15 V external, +5 V local, etc.)

**Signals / connectors:**
- (List key interfaces and expectations.)

**Grounding assumptions:**
- (e.g. ground always common via connector.)

---

## Architectural Summary
**High-level block description:**

- Power input and regulation
- Control / logic blocks
- Actuators (relays, LEDs, outputs)
- Signal routing

(Keep this descriptive, not schematic-level.)

---

## Proven Blocks
The following blocks have been **explicitly validated** under the base contract:

- Block name:
  - Validation method: (current-path analysis / ngspice simulation / bench test)
  - Evidence location: (file, screenshot, commit hash)

---

## Unproven / Under Review
The following blocks **must not be modified or relied upon** without further proof:

- Block name:
  - Open questions:
  - Required validation:

---

## Assumptions
List assumptions that affect correctness:

- (e.g. PROTECT_OK is a hard +15 V rail from host system.)
- (e.g. relay coils energise simultaneously.)

Assumptions must be validated or retired.

---

## Change Log (Design-Relevant)
Record only changes that affect behaviour:

- **Date / Rev:**
  - What changed:
  - Why:
  - Proof invalidated:
  - Proof added:

---

## Do-Not-Change Without Re-Proof
The following must not be altered without explicit re-validation:

- (e.g. relay drive topology)
- (e.g. power sequencing logic)
- (e.g. ground reference scheme)

---

## Open Risks
Known risks or edge cases:

- (e.g. power-down timing, backfeeding risk, etc.)

---

**End of Project Overlay**
