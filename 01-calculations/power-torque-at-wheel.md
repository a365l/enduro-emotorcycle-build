# Power and torque at wheel

## Inputs

| Parameter | Value | Source |
|-----------|-------|--------|
| Bus voltage (nominal) | 72 V | NBPower spec |
| Peak controller current | 450 A | Fardriver ND72450 |
| Continuous controller current | 200 A | Fardriver ND72450 |
| Battery max discharge | 100 A | NBPower spec |
| QS205 winding | 3.5T (50H V3) | Order spec |
| QS205 KV | ~12.9 RPM/V | Derived: QS 5T datasheet = 9.03 KV, scaled ×(5/3.5). Verify with no-load spin test |
| QS205 max torque | 190 Nm | QS Motor 50H V3 datasheet |
| Wheel OD | ~643 mm (r = 0.322 m) | 19" rim + 80/100 tyre, calculated - measure inflated |
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

**Reality check - the battery is the sustained limit.** The pack is rated 100 A, so sustained power is capped at 72 × 100 = **7.2 kW** regardless of what the controller can switch. But peak *torque* at launch is still available: the controller acts like a buck converter, so 450 A of phase current at low speed only draws a fraction of that from the battery. High phase current + low battery current = full launch torque without exceeding the pack rating. Battery current only approaches phase current as speed rises.

## Motor shaft speed (nominal voltage, no load)

```
N = KV * V
N = 12.9 * 72 = ~929 RPM
```

Real RPM under load will be lower due to voltage sag under current.

## Torque at wheel

Peak torque comes from the motor datasheet (190 Nm max) rather than P/ω, which isn't valid near stall. Hub motor is direct drive - ratio 1:1, so only drivetrain efficiency applies:

```
T_wheel = T_motor * n_drive = 190 * 0.95 = ~180 Nm
F_wheel = T_wheel / r_wheel = 180 / 0.322 = ~560 N
```

n_drive ~0.95 for a hub motor (much better than chain drive).

**Traction check:** available rear grip ≈ μ·m·g·(rear weight fraction) ≈ 0.8 × 150 × 9.81 × 0.6 ≈ 705 N on dry hardpack. 560 N of drive force is below that, so peak torque is (just) usable without spinning up - loose surfaces will traction-limit first.

## Predicted 0-30 acceleration

```
a = F_wheel / m_total
t = delta_v / a
```

| Parameter | Value |
|-----------|-------|
| r_wheel | 0.322 m (tyre OD / 2, to be measured inflated) |
| m_total (bike + rider) | ~150 kg (bike est. ~70 kg + rider ~80 kg - weigh the bike) |
| F_wheel (peak) | ~560 N |
| a (ignoring aero drag) | ~3.7 m/s² |
| t_0-30 predicted | **~3.6 s** |
| t_0-30 measured | TBD - first instrumented ride pending |

---

Peak current is burst only - controller derates on heat. In practice acceleration will hit traction limits on loose surfaces before the theoretical peak anyway.
