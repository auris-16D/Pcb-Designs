# Node Verification
## Roksan Kandy KA-1 HT Bypass Project

---

# Purpose

Before designing a HT bypass modification, the **exact signal nodes must be verified** in the amplifier schematic.

Incorrect node identification could introduce:

- DC into the power amplifier
- unwanted loading of circuits
- ground loops
- switching artefacts

This document identifies the **critical nodes that must be confirmed**.

---

# Verification Targets

The HT bypass modification requires verification of four main nodes:

1. Preamp output
2. Power amplifier input
3. VIDEO input routing
4. Speaker protection control

---

# 1. Preamp Output Node

## Objective

Identify the exact node where the **preamp output feeds the power amplifier input**.

## Expected Node

Based on schematic review:

```
L OUT
R OUT
```

These appear to represent the final output of the preamp stage.

Signal path:

```
source input
→ selector IC
→ op-amp stages
→ volume control PCB
→ L OUT / R OUT
```

## Verification Required

Confirm:

- L OUT / R OUT feed the **power amplifier input stage**
- no additional processing exists between these nodes and the power amp

---

# 2. Power Amplifier Input Node

## Objective

Identify the node where the **power amplifier differential input stage receives signal**.

This is where the HT bypass signal must be injected.

## Key Questions

- Is the input **AC-coupled or DC-coupled**?
- What is the **input impedance**?
- Is there any **filtering network** before the differential pair?

## Why This Matters

If the node is DC-coupled:

```
AV processor output
→ direct injection
→ possible DC offset
→ speaker damage risk
```

If AC-coupled:

The existing coupling capacitor protects the stage.

---

# 3. VIDEO Input Routing

## Objective

Confirm how the VIDEO RCA sockets connect into the amplifier.

Expected path:

```
VIDEO RCA
→ input filter network
→ analog switch IC
→ preamp
```

## Verification Required

Confirm:

- VIDEO input is routed through the **selector IC**
- VIDEO input can be **electrically isolated from the selector**

Isolation is required when HT bypass is active.

---

# 4. Speaker Protection Control

## Objective

Identify the node controlling the **speaker protection relay**.

This is needed for **pop suppression during mode switching**.

Desired behaviour:

```
mode switch
→ temporary mute
→ speaker relay open
→ bypass relay switches
→ speaker relay reconnect
```

## Verification Required

Locate:

- speaker relay driver transistor
- protection logic output
- available control signal polarity

---

# Required Supply Rails

The relay switching circuit will require a supply.

Possible rails observed in schematic:

```
+12V
+9V
+5V
-5V
```

Verification needed:

- which rail can safely power the relay
- available current capacity

---

# Ground Reference

HT bypass signal must share the same **signal ground reference** as the existing preamp.

Verify:

```
VIDEO RCA ground
=
preamp signal ground
=
power amp input ground
```

Avoid creating new ground paths.

---

# Summary of Required Verifications

Before design begins confirm:

- [ ] Preamp output nodes (L OUT / R OUT)
- [ ] Power amplifier input node
- [ ] Whether the input stage is AC or DC coupled
- [ ] Power amplifier input impedance
- [ ] VIDEO input routing through selector IC
- [ ] Location of speaker relay control node
- [ ] Suitable relay supply rail
- [ ] Signal ground reference

---

# Design Confidence

```
Current confidence level: Medium
```

Reason:

- amplifier topology understood
- bypass concept well established
- final node verification still required

---

# Next Step

Once the above nodes are verified:

Create the design document:

```
design/relay-bypass-concept.md
```

which will define the HT bypass switching circuit.
