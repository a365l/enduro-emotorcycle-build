# Braking

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Total mass (bike + rider) | [X] kg | Weigh it |
| Entry speed 1 | 30 mph = 13.4 m/s | |
| Entry speed 2 | 50 mph = 22.4 m/s | |
| Measured deceleration | [X] m/s2 | From test below |
| mu (off-road) | ~0.8 | Estimate |

---

## Theoretical max deceleration

```
a_max = mu * g = 0.8 * 9.81 = 7.85 m/s2
```

Tyre-limited max - actual braking depends on brake force and weight transfer.

## Stopping distances

```
s = v^2 / (2 * a)
```

| Entry speed | a = 7.85 m/s2 (theoretical) | a = [measured] |
|-------------|------------------------------|----------------|
| 30 mph | [X] m | [X] m |
| 50 mph | [X] m | [X] m |

---

## Braking test

Mark a start point. Brake hard from a known speed. Measure stopping distance.

| Run | Entry (mph) | Distance (m) | Decel (m/s2) | Date |
|-----|-------------|--------------|--------------|------|
| 1 | | | | |
| 2 | | | | |

---

## Brake setup

| Component | Spec |
|-----------|------|
| Front | [Type, rotor size] |
| Rear | [Type, rotor size] |
| Fluid | Shimano mineral oil (MT501 bleed done Phase 2) |
| Condition after bleed | [Note] |
