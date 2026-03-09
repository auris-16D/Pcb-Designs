# Project Context
## Roksan Kandy KA-1 HT Bypass Modification

---

# Project Objective

Modify a **Roksan Kandy KA-1 Mk1 integrated amplifier** so that the existing **VIDEO input** can function as a **Home Theatre (HT) bypass input** when required.

This allows the amplifier to:

- Power speakers for **two-channel music**
- Act as a **power amplifier for cinema front channels**

while preserving the original audio quality.

---

# System Overview

Current equipment:

- Amplifier: Roksan Kandy KA-1 Mk1
- Speakers: Sonus Faber Grand Piano Home
- Planned addition: AV receiver / cinema processor
- Video projection system

---

# Desired Behaviour

## Integrated Mode

Normal amplifier operation.

```
Selected source
→ Roksan preamp
→ volume control
→ power amplifier
→ speakers
```

VIDEO input behaves as a normal line input.

---

## HT Bypass Mode

VIDEO input becomes direct power amp input.

```
AV receiver front L/R pre-out
→ VIDEO RCA sockets
→ bypass relay
→ power amplifier input
→ speakers
```

The Roksan volume control is bypassed.

Volume controlled by the AV receiver.

---

# Design Goals

- Preserve original amplifier sound
- Avoid unnecessary chassis modification
- Use existing VIDEO RCA sockets
- Maintain safety for speakers
- Ensure reversible modification where possible

---

# Proposed Architecture

Two modes controlled by a **rear panel HT mode switch**.

### Integrated Mode

```
VIDEO RCA
→ selector IC
→ preamp
→ volume
→ power amp
```

### HT Mode

```
VIDEO RCA
→ relay switching
→ power amp input
```

---

# Pop Suppression Strategy

During mode switching:

1. Speaker protection circuit temporarily disconnects speakers
2. Signal routing relay changes state
3. Speakers reconnect after short delay

This prevents switching transients.

---

# Known Facts

- Preamp output nodes labelled **L OUT / R OUT**
- These feed the main power amplifier stage
- Amplifier includes speaker protection relay
- VIDEO input exists on rear panel

---

# Assumptions

- VIDEO input routes through selector IC
- Power amp input is accessible from preamp output node
- Protection circuit can be triggered for temporary mute

---

# Unknowns

- Exact power amp input impedance
- Whether power amp input is AC-coupled
- Exact speaker relay control node

---

# Risks

- Switching noise reaching speakers
- Ground loop between AV receiver and amplifier
- Incorrect node identification causing DC injection

---

# Design Confidence

```
Confidence Level: Medium

Reason:
- amplifier topology understood
- exact nodes still to be verified
```

---

# Next Actions

1. Verify preamp output nodes
2. Verify power amp input coupling
3. Identify protection relay control signal
4. Design relay switching circuit
5. Prototype implementation
