# Top speed prediction

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Motor KV | ~12.9 RPM/V | Derived: QS 5T datasheet = 9.03 KV, scaled ×(5/3.5). Verify with no-load spin test |
| Battery voltage (nominal) | 72 V | NBPower |
| Battery voltage (full charge) | ~84 V if 20S li-ion | Verify pack chemistry/config on label |
| Tyre | 19" x 80/100 | Phase 2 |
| Tyre OD (estimate) | ~643 mm | Calculated below - measure the real thing |
| Drive ratio | 1:1 (hub motor) | |

---

## Tyre geometry

```
19" rim = 19 * 25.4 = 482.6 mm diameter
80/100 tyre: section height = 80% * 100 mm = 80 mm
Tyre OD = 482.6 + 2*80 = ~643 mm
Circumference = pi * 643 = ~2,019 mm = 2.019 m
```

Measure the inflated tyre OD and update this.

## No-load RPM

```
N = KV * V = 12.9 * 72 = ~929 RPM   (nominal)
N = 12.9 * 84 = ~1,084 RPM          (full charge, if 20S)
```

## Predicted top speed (no-load ceiling)

```
v = N * C / 60
v = 929 * 2.019 / 60 = 31.3 m/s = ~70 mph   (nominal voltage)
```

This is the back-EMF ceiling - real top speed will be lower because of motor slip under load, drag, and the battery power limit below.

## Power-limited top speed

At true top speed, drive force = drag + rolling resistance. The sustained power limit is the **battery** (100 A × 72 V = 7.2 kW in), ~6.1 kW at the wheel after motor/controller losses:

```
F_drag = 0.5 * rho * Cd * A * v^2 = 0.343 * v^2
F_roll = Crr * m * g = 0.02 * 150 * 9.81 = ~29 N
Solve: (0.343*v^2 + 29) * v = 6,100 W
  ->  v ≈ 25 m/s = ~56 mph
```

| Parameter | Value |
|-----------|-------|
| Air density | 1.225 kg/m3 |
| Cd (upright rider) | ~0.8 |
| Frontal area A | ~0.7 m2 |
| Crr (knobby on tarmac) | ~0.02 |

**Prediction: ~55 mph sustained on flat tarmac** - power-limited by the pack, comfortably below the ~70 mph back-EMF ceiling. Short bursts above the pack's continuous rating could nudge higher until sag bites.

---

## Measured top speed

| Run | Surface | GPS max (mph) | Date |
|-----|---------|---------------|------|
| 1 | | | |
| 2 | | | |

Racechrono or Harry's LapTimer works fine for this. First instrumented ride pending - drivetrain so far bench-tested suspended on the rig only.
