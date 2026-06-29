# Controller Thermal Estimate

## Fardriver ND72450 Thermal Parameters

| Parameter | Value | Source |
|-----------|-------|--------|
| Controller efficiency (est.) | ~95% | Typical for quality sine-wave FOC |
| Continuous power output | 14.4 kW | 72V × 200A |
| Power dissipated (continuous) | [X] W | P_loss = P_out × (1 - η) / η |
| Thermal shutdown temp | [X] °C | Check Fardriver manual / beep code 8 |
| Heatsink material | Aluminium (blue anodised body) | Observed |

---

## Heat Dissipated at Continuous Rating

```
η = 0.95 (assumed)
P_in = P_out / η = 14,400 / 0.95 = 15,158 W
P_loss = P_in - P_out = 15,158 - 14,400 = 758 W
```

> 758W of heat to dissipate at full continuous load. The blue aluminium body acts as a heatsink — adequate for intermittent trail use, may derate on sustained climbs.

---

## Thermal Resistance Estimate

```
ΔT = P_loss × R_th
R_th = ΔT_allowable / P_loss
```

| Parameter | Value |
|-----------|-------|
| Ambient temp (worst case) | 35 °C |
| Max junction temp | [X] °C (check datasheet) |
| Allowable ΔT | [X - 35] °C |
| Required R_th (case to ambient) | [X] °C/W |

---

## Observed Thermal Behaviour

| Condition | Controller temp (°C) | Duration before derate |
|-----------|---------------------|------------------------|
| Gentle trail | | |
| Hard acceleration | | |
| Sustained hill climb | | |

> Measure with an IR thermometer on the controller body during/after runs.

---

## Notes

- Fardriver fault beep code 8 = controller overtemp
- Controller mounted in airflow? [Yes / No — note mounting position]
- Consider adding airflow ducting if sustained derate observed
