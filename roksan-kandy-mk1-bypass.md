# Project State / Overlay

## Contract Inheritance
This project **inherits and is governed by**:

- `pcb-design-contract.md`

All rules, invariants, and validation requirements in the base contract apply unless explicitly overridden here.

---

## Project Identification
- **Project name:** Roksan Kandy MK1 HT Bypass Modification
- **Repository path:** projects/roksan-kandy-mk1-bypass
- **Current revision:** 0.1 — Concept
- **Status:** Concept

---

## Intent & Scope
**Purpose of this modification:**

- Implement a hardware HT (Home Theatre) bypass on a Roksan Kandy MK1 integrated amplifier
- Expose the pre-amp output and power amp input as rear panel RCA sockets
- Install a front or rear panel switch to select between internal (stereo) and external (HT bypass) signal routing
- Optionally implement an audio signal detection circuit on the main-in socket to automate bypass switching via relay

**Out of scope:**

- Modification of the pre-amp stage circuitry
- Modification of the power amp stage circuitry
- Any change to the phono stage
- Tone or volume control alterations
- Changes to the power supply

---

## External Interfaces
**Power rails:**
- Unknown — to be determined by internal inspection and service documentation
- Assumed: dual rail supply (±V) for power amp stage — requires verification

**Signals / connectors:**
- New: Pre-amp OUT — RCA socket, line level output post volume control
- New: Main IN — RCA socket, line level input direct to power amp stage
- New: Bypass switch — DPDT, selects internal or external signal routing
- Optional: Audio sensing circuit on Main IN for automatic relay switching

**Grounding assumptions:**
- Ground assumed common throughout — requires verification during internal inspection

---

## Architectural Summary
**High-level block description:**

- Locate the internal junction between pre-amp output and power amp input
- Break that junction and route both ends to new rear panel RCA sockets
- Install DPDT switch to reconnect internally (normal stereo) or route via external sockets (HT bypass)
- Optional: Small signal detection sub-circuit monitors Main IN socket; on detecting AC signal drives a relay to switch automatically to bypass mode; relay drops out on signal loss returning to stereo mode

---

## Proven Blocks
None yet. No internal inspection has been carried out. No schematic is available.

---

## Unproven / Under Review

- **Pre/power amp junction location**
  - Open questions: Physical location on PCB unknown. Service manual not publicly available. Signal path not yet traced.
  - Required validation: Internal inspection, signal path tracing with multimeter/oscilloscope, photographic documentation

- **Available voltage rails for relay/sensing circuit**
  - Open questions: Rail voltages unknown. Suitable tap point for small signal circuit not identified.
  - Required validation: Internal inspection and measurement

- **DPDT switch insertion point**
  - Open questions: Physical space for switch on rear or front panel not assessed.
  - Required validation: Internal inspection and physical measurement

- **Auto-sensing relay circuit**
  - Open questions: Full circuit not yet designed. Component values not calculated.
  - Required validation: Block-level ngspice simulation before physical implementation per contract rule 12

---

## Assumptions
- The pre-amp and power amp stages are electrically separable at a single junction point — **not yet verified**
- A suitable low-current power tap exists internally for the optional relay circuit — **not yet verified**
- Ground is common throughout the amplifier — **not yet verified**
- The Roksan Kandy MK1 output is 110W per channel into 8 ohms — stated by user, accepted as verified

---

## Change Log (Design-Relevant)
- **2026-03-06 / Rev 0.1**
  - Initial project state created from design discussion
  - No physical work carried out
  - No proofs established

---

## Do-Not-Change Without Re-Proof
- Nothing established yet — to be populated as blocks are validated

---

## Open Risks
- No service manual or schematic is publicly available; internal topology must be reverse engineered
- Risk of inadvertent ground loop introduction via new RCA sockets — to be assessed during design
- Risk of signal degradation if junction point is incorrectly identified — current path analysis mandatory before any cuts are made per contract rule 8
- Auto-sensing relay circuit must not introduce noise or impedance mismatch into the audio signal path — requires simulation validation before implementation
- Physical modification is irreversible at the point of PCB track cutting — junction must be fully validated before any cuts

---

**End of Project Overlay**
