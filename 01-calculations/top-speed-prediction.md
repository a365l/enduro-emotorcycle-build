# Top speed prediction

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Motor KV | [X] RPM/V | QS205 datasheet - fill this in |
| Battery voltage (nominal) | 72 V | NBPower |
| Battery voltage (full charge) | [X] V | Measure |
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

## No-load RPM at 72V

```
N = KV * V = [KV] * 72 = [X] RPM
```

## Predicted top speed (no-load)

```
v = N * C / 60
v = [N] * 2.019 / 60 = [X] m/s = [X] mph
```

This is the theoretical max - real top speed will be lower because of motor slip under load and aero drag.

## Drag-limited top speed

At true top speed, drive force = drag:

```
F_drag = 0.5 * rho * Cd * A * v^2
```

| Parameter | Value |
|-----------|-------|
| Air density | 1.225 kg/m3 |
| Cd (upright rider) | ~0.8 |
| Frontal area A | ~0.7 m2 |

Solve for v where F_drive = F_drag once you have the motor torque curve.

---

## Measured top speed

| Run | Surface | GPS max (mph) | Date |
|-----|---------|---------------|------|
| 1 | | | |
| 2 | | | |

Racechrono or Harry's LapTimer works fine for this.
