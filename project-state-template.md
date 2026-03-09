# Project State Template

## Project Name

Provide a short descriptive name for the project.

---

# Project Objective

What is the goal of this project?

Examples:

- Design a new PCB
- Modify an existing amplifier
- Analyse a circuit
- Reverse engineer hardware

---

# Known Facts

Facts confirmed through:

- schematics
- measurements
- datasheets
- user confirmation

Example:

- Amplifier model: Roksan Kandy KA-1 Mk1
- Speakers: Sonus Faber Grand Piano Home
- Power amplifier topology: discrete class AB

---

# Assumptions

Temporary beliefs used for reasoning but not yet confirmed.

Example:

- The power amp input may be AC-coupled.
- The video input likely feeds the selector IC.

Assumptions should eventually be **confirmed or removed**.

---

# Inferences

Logical conclusions drawn from known facts.

Example:

- The amplifier preamp and power amp sections are separated by L OUT / R OUT nodes.
- This separation enables potential HT bypass insertion.

---

# Unknowns / Questions

Things that must be confirmed before implementation.

Examples:

- Exact node feeding the power amplifier input
- Input impedance of the power amplifier stage
- Available supply rails for relay control

---

# Design Constraints

Constraints that limit design choices.

Examples:

- Must preserve original amplifier sound quality
- Must avoid drilling new holes in chassis
- Must remain reversible if possible

---

# Risks

Potential problems or hazards.

Examples:

- Ground loop between AV receiver and amplifier
- DC offset injection into power amp
- Switching noise damaging speakers

---

# Design Decisions

Record any agreed decisions.

Example:

- Use existing VIDEO RCA sockets for HT bypass
- Implement relay-based switching
- Use speaker protection circuit for pop suppression

---

# Verification Checklist (New)

Before implementing a circuit modification confirm:

- [ ] Exact schematic node identified
- [ ] AC or DC coupling verified
- [ ] Input impedance known
- [ ] Supply rails identified
- [ ] Protection circuits understood

---

# Design Confidence (New)

Confidence level for the current design state.

Example:

```
Confidence Level: Medium

Reason:
- schematic mostly verified
- some nodes still need confirmation
```

---

# Next Actions

Concrete next steps.

Examples:

- Verify preamp output node
- Identify speaker relay control signal
- Design relay switching circuit
- Prototype modification

---

# Notes

Additional observations, thoughts, or references.

This section acts as the project's engineering notebook.
