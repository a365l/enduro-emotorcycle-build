# Wiring Gauge Calculation

## Requirements

| Circuit | Current (continuous) | Current (peak) |
|---------|---------------------|----------------|
| Battery to controller (power) | 100 A (battery limited) | 200 A |
| Phase wires (motor) | 200 A | 450 A |
| Signal wiring (throttle, hall, etc.) | < 1 A | < 1 A |

---

## Power Cable Sizing

For copper cable, a conservative allowable current density is **~3–4 A/mm²** for enclosed/bundled runs (more conservative than free-air ratings).

```
Required area = I_continuous / J_allowable
```

| Circuit | I (A) | J (A/mm²) | Min area (mm²) | AWG equiv | Chosen cable |
|---------|-------|-----------|---------------|-----------|-------------|
| Battery → controller (power) | 100 | 3.5 | 28.6 mm² | AWG 2 (33.6mm²) | [What did you use?] |
| Phase wires (peak 450A burst) | 200 cont | 3.5 | 57 mm² | AWG 1/0 (53.5mm²) | [What did you use? — QS205 likely comes with correct gauge] |

> Note: Phase wire current rating is motor-side — the QS205 ships with phase wires. Record gauge here.

---

## Voltage Drop Check

```
V_drop = I × R
R = ρ × L / A    (ρ_copper = 1.72 × 10⁻⁸ Ω·m)
```

| Run | I (A) | Length (m) | Area (mm²) | V_drop (V) | % of 72V |
|-----|-------|-----------|-----------|-----------|----------|
| Battery → controller | 100 | [X] | [X] | [X] | [X]% |

> Target: < 2% voltage drop (< 1.44V at 72V)

---

## Connector Ratings

| Connector | Used for | Rated current | Actual current |
|-----------|----------|---------------|----------------|
| XT90 / [type] | Battery main | [X] A | 100 A |
| Phase connectors | Motor phase | [X] A | 200 A cont |
| Molex (Fardriver signal) | Signal harness | < 5 A | < 1 A |
