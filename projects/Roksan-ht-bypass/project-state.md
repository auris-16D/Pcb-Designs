# Project State
## Roksan Kandy KA-1 HT Bypass Modification

---

# Project Status

Phase: Analysis  
Design Confidence: Medium  
Implementation Approved: No  

---

# Project Objective

Modify a **Roksan Kandy KA-1 Mk1 integrated amplifier** so the existing **VIDEO input** can optionally operate as a **Home Theatre (HT) bypass input**.

This will allow the amplifier to:

- Drive speakers normally for **two-channel music**
- Act as a **power amplifier for the front channels of a cinema system**

while preserving the amplifier’s existing sound quality.

---

# System Overview

Current equipment:

Amplifier  
- Roksan Kandy KA-1 Mk1

Speakers  
- Sonus Faber Grand Piano Home (walnut)

Future system components

- AV receiver or cinema processor
- Projector-based cinema system

Goal

Use **one pair of speakers for both music and cinema** without degrading music performance.

---

# Desired Behaviour

## Integrated Mode (Normal Operation)

Amplifier behaves exactly as designed.

Signal flow:

```
Selected source
→ Roksan input selector
→ preamp stages
→ volume control
→ power amplifier
→ speakers
```

VIDEO input behaves as a **standard line-level input**.

---

## HT Bypass Mode

VIDEO input becomes a **direct power amplifier input**.

Signal flow:

```
AV receiver front L/R pre-out
→ VIDEO RCA sockets
→ bypass relay
→ power amplifier input
→ speakers
```

Key behaviour

- Roksan preamp is bypassed
- Roksan volume control is bypassed
- Volume controlled by the AV receiver

---

# Design Goals

- Preserve the **existing Roksan sound signature**
- Avoid unnecessary modification of the amplifier chassis
- Reuse the **existing VIDEO RCA sockets**
- Prevent switching noise reaching the speakers
- Maintain a **reversible modification where possible**
- Ensure compatibility with AV receiver pre-outs

---

# Proposed Architecture

The modification introduces:

- A **relay-based signal routing stage**
- A **rear panel mode switch**
- Integration with the **existing speaker protection relay for pop suppression**

---

## Integrated Mode

VIDEO input routed normally.

```
VIDEO RCA
→ selector IC
→ preamp
→ volume
→ power amp
```

---

## HT Bypass Mode

VIDEO input routed directly to the power amplifier input.

```
VIDEO RCA
→ relay switching
→ power amp input
```

Preamp output is disconnected from the power amp input in this mode.

---

# Pop Suppression Strategy

To protect the speakers from switching transients:

1. Mode switch triggers a **temporary mute**
2. Speaker protection relay disconnects speakers
3. Signal routing relay changes state
4. Short delay expires
5. Speaker relay reconnects speakers

This prevents switching artefacts reaching the speakers.

---

# Known Facts

- Amplifier model: **Roksan Kandy KA-1 Mk1**
- Preamp output nodes labelled **L OUT / R OUT**
- These feed the **main power amplifier input**
- Amplifier contains **speaker protection relays**
- VIDEO input exists on rear panel
- Amplifier is approximately **25 years old**
- Amplifier topology is **discrete class AB**

---

# Assumptions

These must be verified before implementation.

- VIDEO RCA sockets feed the **input selector IC**
- Preamp and power amp sections are separated at **L OUT / R OUT**
- Power amplifier input impedance is suitable for AV receiver output
- Speaker protection relay control signal is accessible

---

# Inferences

Based on schematic review:

- The amplifier has a **clear preamp → power amp boundary**
- This boundary allows insertion of a **relay switching stage**
- The VIDEO input is a convenient candidate for HT bypass

---

# Unknowns / Questions

These must be verified before implementation.

- Is the **power amp input AC or DC coupled**
- Exact **power amp input impedance**
- Exact **speaker protection relay control node**
- Whether VIDEO input routing can be safely isolated from the selector IC
- Available **supply rail for relay control**

---

# Design Constraints

- Modification must not degrade audio quality
- Modification should be **reversible**
- Existing chassis should not be modified unnecessarily
- Must maintain safe operation with valuable speakers

---

# Risks

Potential technical risks:

- Switching transient reaching speakers
- Ground loop between AV receiver and amplifier
- Incorrect node identification introducing DC into the power amp
- Selector circuit interaction with bypass signal

---

# Verification Checklist

Before implementing the modification confirm:

- [ ] Exact **preamp output node**
- [ ] Exact **power amplifier input node**
- [ ] Whether the input stage is **AC or DC coupled**
- [ ] Input impedance of the power amp
- [ ] Location of speaker relay control
- [ ] Suitable supply rail for relay control

---

# Design Confidence

Current confidence level:

```
Confidence Level: Medium
```

Reason:

- Overall amplifier topology is understood
- HT bypass architecture is well established
- Exact nodes and coupling still need confirmation

---

# Next Actions

1. Verify **preamp output nodes**
2. Verify **power amp input coupling**
3. Identify **speaker protection relay control signal**
4. Confirm **VIDEO input routing**
5. Design relay switching circuit
6. Prototype modification

---

# Notes

This project follows the repository engineering workflow:

```
analysis → verified design → implementation
```

Design work should not proceed to implementation until the **verification checklist is complete**.
