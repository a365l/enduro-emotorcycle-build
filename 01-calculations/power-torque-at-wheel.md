# Power and torque at wheel

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Bus voltage (nominal) | 72 V | NBPower spec |
| Peak controller current | 450 A | Fardriver ND72450 |
| Continuous controller current | 200 A | Fardriver ND72450 |
| QS205 KV rating | [X] RPM/V | Look up in QS Motor datasheet |
| Wheel OD | [X] mm | Measure - 19" rim + 80/100 tyre |
| Drive ratio | 1:1 (hub motor, direct drive) | |

---

## Peak electrical power

```
P_peak = V * I_peak
P_peak = 72 * 450 = 32,400 W = 32.4 kW = 43.4 hp
```

## Continuous electrical power

```
P_cont = V * I_cont
P_cont = 72 * 200 = 14,400 W = 14.4 kW = 19.3 hp
```

## Motor shaft speed (nominal voltage, no load)

```
N = KV * V
N = [KV] * 72 = [X] RPM
```

Real RPM under load will be lower due to voltage sag under current.

## Torque at motor shaft (peak)

```
T_motor = P_peak / w
w = 2*pi * N / 60   [rad/s]
T_motor = 32400 / w = [X] Nm
```

## Torque at wheel

Hub motor is direct drive - ratio is 1:1. Just account for drivetrain efficiency:

```
T_wheel = T_motor * n_drive
```

n_drive ~0.95 for a hub motor (much better than chain drive).

## Predicted 0-30 acceleration

```
F_wheel = T_wheel / r_wheel
a = F_wheel / m_total
t = delta_v / a
```

| Parameter | Value |
|-----------|-------|
| r_wheel | [X] m (tyre OD / 2) |
| m_total (bike + rider) | [X] kg |
| F_wheel (peak) | [X] N |
| a (ignoring aero drag) | [X] m/s2 |
| t_0-30 predicted | [X] s |
| t_0-30 measured | [X] s |

---

Peak current is burst only - controller derates on heat. In practice acceleration will hit traction limits before the theoretical peak anyway.
