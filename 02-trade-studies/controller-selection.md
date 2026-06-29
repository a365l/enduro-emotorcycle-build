# Trade Study: Controller Selection

## Decision

Selected: **Fardriver ND72450** (72V, 200A continuous, 450A peak)

Date: [Phase 2]

---

## Options Considered

| Option | Voltage | Cont. current | Peak current | Programmable | Cost | Notes |
|--------|---------|--------------|-------------|--------------|------|-------|
| Fardriver ND72450 | 72V | 200A | 450A | Yes (BT + PC) | £[X] | Selected |
| Generic sine wave (Phase 0) | 72V | 80A | ~100A | No | £[X] | Replaced - bottleneck |
| Kelly KLS7275N | 72V | 250A | 500A | Yes | £[X] | Alternative considered? |
| [Other option] | | | | | | |

---

## Selection Rationale

**Why Fardriver over generic controller?**
- Phase 0 generic 80A controller was limiting the battery (rated 100A) and motor
- Fardriver rated 200A continuous / 450A peak - removes the bottleneck entirely
- Field-oriented control (FOC) / sine wave = smooth power delivery vs square wave
- Bluetooth + PC programming: tunable throttle response, current limits, speed modes
- Labelled Molex connectors for every function vs generic unlabelled wiring
- Active fault diagnostic via beep codes

**Why ND72450 specifically?**
- 72V matches existing battery
- 450A peak suitable for QS205 motor
- Well-documented in the Surron/enduro EV community

---

## Key Specs

| Spec | Value |
|------|-------|
| Voltage | 72V |
| Continuous phase current | 200A |
| Peak phase current | 450A |
| Control mode | FOC sine wave |
| Programming | Bluetooth app + PC software |
| Connectors | Labelled Molex signal harness |
| Fault codes | 8-beep diagnostic system |
| Thermal protection | Yes (beep code 8) |

---

## Lessons

- Autolearn must be run every time motor or controller is swapped
- Surron throttle wiring does not match Fardriver throttle input pin-for-pin - map before crimping
- Beep codes are genuinely useful for diagnosing issues without a laptop
