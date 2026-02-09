# PCB Design Contract (Generic)

## Purpose
This contract governs *how* PCB designs are reasoned about, modified, and validated.
It applies to **all** projects, regardless of function or complexity.

---

## 1. Scope & Authority
1. This document is the **authoritative governance** for all PCB design work.
2. Project-specific documents may add constraints but **must not contradict** this contract.
3. In case of conflict, this contract **prevails**.

---

## 2. Core Invariants
4. **Net names do not imply function**; only conductive paths do.
5. **Control** and **power** paths must be explicitly distinguishable.
6. Grounds are assumed **common** unless explicitly stated otherwise.
7. Every actuator (relay, LED, regulator, output, driver) must have:
   - a defined **source**,
   - a defined **sink**,
   - and a defined **enable condition**.

---

## 3. Electrical Reasoning Rules
8. No behavioural claim is valid without **explicit current-path analysis**.
9. “Looks right” or visual intuition is **not proof**.
10. A component separates nets unless it is copper:
    - Resistors, diodes, transistors, ICs **always** separate nets.
11. Dynamic behaviour (enable, delay, gating, sequencing) must be proven by:
    - step-by-step current flow analysis **or**
    - KiCad/ngspice simulation of the relevant block.

---

## 4. Validation Requirements
12. **Simulation is mandatory** for any claim involving:
    - enable/disable logic,
    - timing/delays,
    - power sequencing,
    - gating of supplies or actuators.
13. Simulations may be **block-level**; full-board simulation is not required.
14. Simulation results must map back to **named schematic nets**.

---

## 5. Change Control
15. No component may be removed unless:
    - its function is explicitly identified, and
    - a replacement mechanism is explicitly identified and validated.
16. Refactors must state:
    - what changed,
    - why it changed,
    - which proofs are invalidated and must be redone.
17. Schematic and PCB **must be in sync** before conclusions are drawn.

---

## 6. Review Discipline
18. Ambiguity must be surfaced early; assumptions must be stated explicitly.
19. If evidence is insufficient, the correct response is **to ask**, not infer.
20. All conclusions must be traceable to:
    - schematic connectivity,
    - PCB net tracing,
    - or simulation evidence.

---

## 7. Working Model
21. The assistant acts as a **fallible reviewer**, not an authority.
22. All advice is provisional until proven under this contract.
23. Proof overrides precedent, intuition, and prior discussion.

---

## 8. Adoption
24. Any project that references this file is deemed to **inherit** it in full.
25. Deviations must be documented and justified in the project overlay.

---

**End of Contract**
