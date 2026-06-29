# Power & Torque at Wheel

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Bus voltage (nominal) | 72 V | NBPower spec |
| Peak controller current | 450 A | Fardriver ND72450 spec |
| Continuous controller current | 200 A | Fardriver ND72450 spec |
| Motor: QS205 KV rating | [X] RPM/V | QS Motor datasheet — measure or look up |
| Wheel diameter (tyre OD) | [X] mm | Measure — 19" rim + 80/100 tyre |
| Drive reduction ratio | 1:1 (hub motor, direct drive) | |

---

## Peak Electrical Power

```
P_peak = V × I_peak
P_peak = 72 × 450 = 32,400 W = 32.4 kW ≈ 43.4 hp
```

## Continuous Electrical Power

```
P_cont = V × I_cont
P_cont = 72 × 200 = 14,400 W = 14.4 kW ≈ 19.3 hp
```

## Motor Shaft Speed (at nominal voltage)

```
N = KV × V_nominal
N = [KV] × 72 = [X] RPM
```

> Fill in KV from QS205 datasheet. Note: actual RPM will be lower under load due to voltage sag.

## Wheel Speed & Top Speed Prediction

See `top-speed-prediction.md`

## Torque at Motor Shaft (peak)

```
T_motor = P_peak / ω
ω = 2π × N / 60  [rad/s]
T_motor = 32400 / ω = [X] Nm
```

## Torque at Wheel (hub motor = direct drive, ratio = 1:1)

```
T_wheel = T_motor × η_drive
```

> Estimate η_drive ≈ 0.95 for hub motor (low transmission losses vs chain drive)

## Predicted Acceleration (0–30 mph)

```
F_wheel = T_wheel / r_wheel
a = F_wheel / m_total
t_0-30 = Δv / a
```

| Parameter | Value |
|-----------|-------|
| r_wheel | [X] m (measure tyre OD / 2) |
| m_total (bike + rider) | [X] kg |
| F_wheel (peak) | [X] N |
| a (peak, ignoring drag) | [X] m/s² |
| t_0–30 mph predicted | [X] s |
| t_0–30 mph measured | [X] s |

---

## Notes

- Peak current only sustainable for short bursts — controller will derate at high temperature
- Real acceleration will be drag and traction limited before theoretical peak
