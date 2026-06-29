# Battery Capacity & Range

## Battery Spec

| Parameter | Value |
|-----------|-------|
| Nominal voltage | 72 V |
| Capacity | 30 Ah |
| Max discharge rate | 100 A |
| Chemistry | [Li-ion / LiFePO4 — check NBPower spec] |
| Wh capacity | 72 × 30 = **2,160 Wh = 2.16 kWh** |

---

## Usable Energy

Batteries are typically not discharged to 0% (reduces cycle life).

```
E_usable = 2160 × DoD
```

| Depth of Discharge (DoD) | Usable Energy |
|--------------------------|---------------|
| 80% (conservative) | 1,728 Wh |
| 90% (typical) | 1,944 Wh |
| 100% (not recommended) | 2,160 Wh |

---

## Range Estimate

Energy consumption depends heavily on riding style and terrain.

| Riding Style | Est. Consumption (Wh/km) | Predicted Range (80% DoD) |
|-------------|--------------------------|---------------------------|
| Gentle trail | ~40 Wh/km | ~43 km |
| Hard trail / enduro | ~70–100 Wh/km | ~17–25 km |
| Flat road | ~25–35 Wh/km | ~50–70 km |

> **Measure actual consumption**: log battery voltage before and after a known-distance run. Calculate Wh used and divide by distance.

## Measured Consumption

| Run | Distance (km) | Start Voltage | End Voltage | Est. Wh Used | Wh/km |
|-----|--------------|--------------|-------------|--------------|-------|
| 1 | | | | | |
| 2 | | | | | |

---

## Current Limits

```
Max battery discharge current = 100 A
Max controller continuous = 200 A
```

> Battery is the limiting factor at sustained load — 100A × 72V = 7.2kW sustainable from pack.
> Controller peak 450A bursts will sag the battery voltage — measure voltage under peak load.

## Voltage Sag Under Load

| Condition | Voltage |
|-----------|--------|
| Resting (full) | [X] V |
| Under 100A load | [X] V |
| Under peak load (brief) | [X] V |

> Measure with a multimeter or data logger while riding.
