# Battery capacity and range

## Pack spec

| Parameter | Value |
|-----------|-------|
| Nominal voltage | 72 V |
| Capacity | 30 Ah |
| Max discharge | 100 A |
| Chemistry | [Check the NBPower label - Li-ion or LiFePO4] |
| Total energy | 72 * 30 = **2,160 Wh = 2.16 kWh** |

---

## Usable energy

Don't discharge to zero - it kills cycle life. In practice work with 80-90% DoD.

| DoD | Usable energy |
|-----|---------------|
| 80% | 1,728 Wh |
| 90% | 1,944 Wh |
| 100% (avoid) | 2,160 Wh |

---

## Range estimate

Varies a lot depending on how hard you're riding.

| Riding style | Est. consumption (Wh/km) | Range at 80% DoD |
|-------------|--------------------------|------------------|
| Easy trail | ~40 Wh/km | ~43 km |
| Hard enduro / climbing | ~70-100 Wh/km | ~17-25 km |
| Flat road | ~25-35 Wh/km | ~50-70 km |

Measure actual consumption by logging voltage before and after a known-distance run.

## Measured consumption log

| Run | Distance (km) | Start voltage | End voltage | Wh used | Wh/km |
|-----|---------------|---------------|-------------|---------|-------|
| 1 | | | | | |
| 2 | | | | | |

---

## Current limits

The battery limits sustained current more than the controller does:

```
Battery max: 100A
Controller continuous: 200A
Controller peak: 450A

Sustained limit from pack = 100A * 72V = 7.2 kW
```

At peak current the battery voltage will sag - worth measuring.

## Voltage sag under load

| Condition | Voltage |
|-----------|----------|
| Resting (full) | [X] V |
| Under 100A | [X] V |
| Brief peak | [X] V |

Measure with a multimeter on the main leads, or add a data logger.
