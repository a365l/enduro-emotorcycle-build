# Top Speed Prediction

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Motor KV | [X] RPM/V | QS205 datasheet / measure |
| Battery voltage (nominal) | 72 V | NBPower |
| Battery voltage (full charge) | [X] V | Measure |
| Tyre size | 19" × 80/100 | Phase 2 fitment |
| Tyre OD (estimated) | [X] mm | Measure inflated |
| Drive reduction | 1:1 (hub motor) | |

---

## Predicted No-Load RPM

```
N_no_load = KV × V_nominal
N_no_load = [KV] × 72 = [X] RPM
```

## Wheel Circumference

```
19" rim → rim diameter = 19 × 25.4 = 482.6 mm
Tyre OD (80/100-19): section height = 80% × 100mm = 80mm
Tyre OD = 482.6 + 2 × 80 = ~643 mm
Circumference = π × 643 = ~2,019 mm = 2.019 m
```

> Measure actual inflated tyre OD and update above.

## Predicted Top Speed (no-load)

```
v = N × C / 60
v = [N_no_load] × 2.019 / 60 = [X] m/s = [X] mph
```

> Real top speed will be lower — motor slips under load, and aerodynamic drag limits speed.

## Drag-Limited Top Speed

At top speed, drive force = drag force.

```
F_drag = 0.5 × ρ × Cd × A × v²
```

| Parameter | Value |
|-----------|-------|
| Air density ρ | 1.225 kg/m³ |
| Drag coefficient Cd | ~0.8 (upright motorbike + rider) |
| Frontal area A | ~0.7 m² (estimate) |
| Drive force at top speed | [X] N |

> Solve for v where F_drive = F_drag. Fill in once F_drive at speed is known from motor curve.

---

## Measured Top Speed

| Run | Condition | GPS speed (mph) | Date |
|-----|-----------|----------------|------|
| 1 | | | |
| 2 | | | |

> Use a GPS app (e.g. Racechrono, Harry's LapTimer, or phone GPS) to log actual top speed.
