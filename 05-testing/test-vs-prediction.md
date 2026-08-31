# Test vs Prediction

Running comparison of calculated predictions against measured results.

**Status:** Drivetrain bench-tested suspended on the rig (autolearn complete, wiring verified against fault codes). First instrumented ride pending - measured columns fill in then.

---

## Performance

| Metric | Method | Predicted | Measured | Difference | Date |
|--------|--------|-----------|----------|------------|------|
| Top speed (flat) | GPS | ~55 mph | | | |
| 0–30 mph time | Timer | ~3.6 s | | | |
| Range (trail riding) | Odometer + battery log | ~17-25 km | | | |
| Range (gentle) | Odometer + battery log | ~43 km | | | |
| Wh/km (trail) | Battery log | ~70-100 Wh/km | | | |

Predictions from: [top speed](../01-calculations/top-speed-prediction.md) · [power & torque](../01-calculations/power-torque-at-wheel.md) · [range](../01-calculations/battery-capacity-range.md)

---

## Electrical

| Metric | Predicted | Measured | Date |
|--------|-----------|----------|------|
| Resting battery voltage (full) | ~84 V (if 20S li-ion - verify) | | |
| Battery voltage under 100A load | ~78-80 V (est. sag) | | |
| Controller temp after 10 min trail | < thermal cutout (beep code 8) | | |
| Peak current draw (Fardriver app) | ≤300 A phase (configured limit; launch, briefly) | | |

---

## Calculations Reference

- Power & torque: `../01-calculations/power-torque-at-wheel.md`
- Range: `../01-calculations/battery-capacity-range.md`
- Top speed: `../01-calculations/top-speed-prediction.md`
- Braking: `../01-calculations/braking.md`
