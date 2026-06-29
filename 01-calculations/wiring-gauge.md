# Wiring gauge

## Current requirements

| Circuit | Continuous | Peak |
|---------|-----------|------|
| Battery to controller | 100 A (pack limited) | 200 A |
| Phase wires (motor) | 200 A | 450 A |
| Signal wiring | < 1 A | < 1 A |

---

## Power cable sizing

Safe allowance for copper in a bundled vehicle run is about 3-4 A/mm2.

```
Min cross-section = I / J
```

| Circuit | I (A) | J (A/mm2) | Min area (mm2) | AWG equiv | What's fitted |
|---------|-------|-----------|----------------|-----------|---------------|
| Battery to controller | 100 | 3.5 | 28.6 | AWG 2 (33.6 mm2) | [note what you used] |
| Phase wires | 200 cont | 3.5 | 57 | AWG 1/0 (53.5 mm2) | [QS205 ships with these - note the gauge] |

---

## Voltage drop check

```
V_drop = I * R
R = rho * L / A     (rho_copper = 1.72e-8 ohm.m)
```

| Run | I (A) | Length (m) | Area (mm2) | V_drop (V) | % of 72V |
|-----|-------|------------|------------|------------|----------|
| Battery to controller | 100 | [X] | [X] | [X] | [X]% |

Keep under 2% (under 1.44V at 72V).

---

## Connector ratings

| Connector | Used for | Rated current | Actual current |
|-----------|----------|---------------|----------------|
| XT90 / [type] | Battery main | [X] A | 100 A |
| Phase connectors | Motor phases | [X] A | 200 A cont |
| Molex (signal) | Fardriver harness | < 5 A | < 1 A |
