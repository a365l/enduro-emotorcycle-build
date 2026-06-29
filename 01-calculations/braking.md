# Braking Distance Calculation

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Total mass (bike + rider) | [X] kg | Weigh on scales |
| Entry speed | 30 mph = 13.4 m/s | |
| Entry speed | 50 mph = 22.4 m/s | |
| Braking deceleration | [X] m/s² | Measure or estimate |
| Coefficient of friction (μ) | ~0.8 (off-road trail) | Estimate |

---

## Theoretical Maximum Deceleration

```
a_max = μ × g = 0.8 × 9.81 = 7.85 m/s²
```

> This is the tyre-limited maximum — actual braking depends on brake force and weight transfer.

## Stopping Distance Formula

```
s = v² / (2 × a)
```

| Entry Speed | a = 7.85 m/s² (theoretical) | a = [measured] m/s² |
|-------------|-----------------------------|-----------------------|
| 30 mph (13.4 m/s) | [X] m | [X] m |
| 50 mph (22.4 m/s) | [X] m | [X] m |

---

## Measured Braking Test

Method: mark start point, brake hard from known speed, measure distance to stop.

| Run | Entry speed (mph) | Stopping distance (m) | Deceleration (m/s²) | Date |
|-----|-------------------|----------------------|---------------------|------|
| 1 | | | | |
| 2 | | | | |

---

## Brake System

| Component | Spec |
|-----------|------|
| Front brake | [Type, rotor size] |
| Rear brake | [Type, rotor size] |
| Brake fluid | Shimano mineral oil (MT501 bleed — Phase 2) |
| Condition after bleed | [Note] |
