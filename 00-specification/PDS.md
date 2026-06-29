# Product Design Specification — Enduro E-Motorcycle

## Project Overview

Full DIY enduro electric motorcycle build. Starting from donor ICE enduro frames, replacing drivetrain with hub motor, lithium battery, and programmable sine-wave controller. Target: rideable off-road electric enduro capable of trail use.

---

## Performance Requirements

| ID | Requirement | Target | Measured | Status |
|----|-------------|--------|----------|--------|
| P-001 | Top speed (flat) | > [X] mph | | ☐ |
| P-002 | Range (trail riding) | > [X] km | | ☐ |
| P-003 | 0–30 mph time | < [X] s | | ☐ |
| P-004 | Climbable gradient | > [X]° | | ☐ |
| P-005 | Kerb weight (ready to ride) | < [X] kg | | ☐ |

---

## Electrical Requirements

| ID | Requirement | Target | Status |
|----|-------------|--------|--------|
| E-001 | Bus voltage | 72V nominal | ✓ |
| E-002 | Peak current (controller) | 450A | ✓ (Fardriver ND72450) |
| E-003 | Continuous current | 200A | ✓ |
| E-004 | Battery capacity | ≥ 2kWh | ✓ (2.16kWh) |
| E-005 | Battery max discharge rate | ≥ 100A | ✓ (NBPower 100A) |
| E-006 | Wiring: all connections serviceable without soldering | Crimped terminals | ✓ (Phase 2) |

---

## Safety Requirements

| ID | Requirement | Status |
|----|-------------|--------|
| S-001 | Battery pack fused | ☐ |
| S-002 | Phase wire insulation rated for voltage | ☐ |
| S-003 | Controller thermally protected | ✓ (Fardriver onboard temp protection) |
| S-004 | Braking system functional before any powered test | ✓ |
| S-005 | No exposed HV terminals | ☐ |

---

## Constraints

- Budget: [£X total across phases]
- Must use existing donor frame
- Must be transportable in [vehicle type]
- Off-road use only (no road legal requirement)

---

## Out of Scope

- Road registration / type approval
- ABS braking
- Regenerative braking (Fardriver capable but not configured this phase)
