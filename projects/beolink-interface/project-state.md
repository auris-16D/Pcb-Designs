# Project State / Overlay

## Contract Inheritance
This project **inherits and is governed by**:

- `pcb-design-contract.md`

All rules, invariants, and validation requirements in the base contract apply unless explicitly overridden here.

---

## Project Identification
- **Project name:** Beolink Relay Interface (B&O to non-B&O amplifier)
- **Repository path:** projects/beolink-relay-interface/
- **Current revision:** Rev-B (in progress)
- **Status:** Schematic + PCB under active refactor

---

## Intent & Scope
**Purpose of this PCB:**
- Interface a Bang & Olufsen Beolink 8-pin DIN output to standard RCA outputs.
- Provide relay-based audio routing and muting.
- Generate a 5 V DIN_TRIG signal for downstream equipment.
- Ensure outputs only become active when the host Beomaster is awake and the user explicitly enables the interface.

**Out of scope:**
- Audio amplification.
- Beomaster internal protection or fault handling.
- Powering external loads from the Beomaster rails.

---

## External Interfaces
**Power rails:**
- `PROTECT_OK`: +15 V hard rail from Beomaster, present only when its main relay is energised.
- `+15_BEOLINK_SEL`: Same +15 V rail, routed to the PCB via a user switch.
- Local +5 V derived on-board via linear regulator.

**Signals / connectors:**
- Beolink DIN (audio L/R, ground, PROTECT_OK).
- RCA outputs.
- DIN_TRIG (5 V logic output).

**Grounding assumptions:**
- Ground is always common between Beomaster and this PCB via the DIN cable.

---

## Architectural Summary
**High-level blocks:**
- Power entry via +15_BEOLINK_SEL with bleeder to ground.
- Linear regulation to +5 V.
- Relay coil drive (low-side NPN sink).
- Relay-based audio routing.
- DIN_TRIG generation with delay network.
- Status indication (bi-colour LED).

---

## Proven Blocks
The following blocks have been **explicitly validated by schematic + PCB net tracing**:

- **Relay coil low-side switching (Q1):**
  - Q1 collector is on the relay coil return net shared with K1/K2 pin 10.
  - Q1 emitter is on GND.
  - Q1 base is driven via R1 from RELAY_EN.
  - When RELAY_EN is high, Q1 sinks the coil return and energises both relays.
  - Validation method: explicit net tracing in KiCad (highlight-net).

- **Relay energisation dependency on +15_BEOLINK_SEL:**
  - Relay coils are powered from +15_BEOLINK_SEL.
  - Without +15_BEOLINK_SEL present, relays cannot energise regardless of logic state.
  - Validation method: current-path analysis.

---

## Unproven / Under Review
The following require **simulation or further proof** before being considered locked:

- **RELAY_EN generation logic:**
  - Interaction between +15_BEOLINK_SEL, PROTECT_OK, diode ORing, and pull-downs.
  - Required validation: ngspice simulation or stepwise current-path proof for all power-up and power-down cases.

- **DIN_TRIG delay and inhibit behaviour:**
  - Correct timing and gating relative to relay energisation and PROTECT_OK.
  - Required validation: ngspice transient simulation.

---

## Assumptions
The following assumptions are currently relied upon and must remain true:

- PROTECT_OK is a hard +15 V rail capable of sourcing small control currents.
- User switch only routes +15, not ground.
- Both relays always energise together.
- Relay coils are tolerant of operation from +15 V with no series resistor.

---

## Change Log (Design-Relevant)
- **Rev-B (current):**
  - Refactored understanding of Q1 as the relay coil low-side sink.
  - Identified relay coil return net as distinct from RELAY_EN.
  - Proof invalidated: prior assumptions about Q1 being redundant.
  - Proof added: PCB net tracing confirming Q1 collector on coil return.

---

## Do-Not-Change Without Re-Proof
The following must not be altered without explicit re-validation:

- Relay coil drive topology (Q1 + coil return net).
- Power sourcing of relay coils from +15_BEOLINK_SEL.
- Ground reference scheme (single common ground via DIN).

---

## Open Risks
- Undefined behaviour during rapid power cycling (PROTECT_OK vs +15_BEOLINK_SEL timing).
- Potential backfeeding paths via protection diodes (requires simulation).
- DIN_TRIG asserting earlier or later than intended relative to relay contacts.

---

**End of Project Overlay**
