# Controller thermal

## Heat at continuous rating

Assuming 95% efficiency (typical for a good FOC controller):

```
P_in = P_out / n = 14,400 / 0.95 = 15,158 W
P_loss = P_in - P_out = 758 W
```

758W to shift at full continuous load. The blue anodised aluminium body is the heatsink - fine for trail use with natural breaks, might derate on a long sustained climb.

---

## Parameters

| Parameter | Value | Source |
|-----------|-------|--------|
| Assumed efficiency | 95% | Typical FOC |
| Continuous P_in | 15,158 W | Calculated |
| Heat dissipated (continuous) | 758 W | Calculated |
| Thermal shutdown temp | [X] °C | Check Fardriver manual - beep code 8 |
| Heatsink | Blue anodised aluminium body | Observed |

---

## Thermal resistance

```
dT = P_loss * R_th
R_th needed = dT_allowable / P_loss
```

| Parameter | Value |
|-----------|-------|
| Ambient (worst case) | 35 °C |
| Max controller temp | [X] °C |
| Allowable dT | [X] °C |
| Required R_th | [X] °C/W |

---

## Measured behaviour

| Condition | Controller temp (°C) | Time before derate |
|-----------|---------------------|--------------------|
| Easy trail | | |
| Hard acceleration | | |
| Sustained climb | | |

Measure with an IR thermometer on the controller body after a run.

---

Fardriver beep code 8 = controller too hot. If you're hitting it regularly, sort out more airflow around the controller.
