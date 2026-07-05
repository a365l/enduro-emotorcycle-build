# Trade Study: Motor Selection

## Decision

Selected: **QS Motor QS205 50H V3, 3.5T winding** hub motor (150 mm dropout, 19×1.6 rim)

Date: Phase 2 (June 2026)

---

## Options Considered

| Option | Type | Rated / peak power | Weight | Notes |
|--------|------|-------------------|--------|-------|
| QS Motor QS205 50H V3 3.5T | Hub (rear) | 3 kW / ~6 kW | ~14 kg | **Selected** |
| Generic hub motor (Phase 0) | Hub (rear) | ~3-4 kW claimed | unverified | Too weak in practice, replaced |
| QS138 70H class mid-drive | Mid-drive | 3 kW / ~8 kW | ~9 kg + drivetrain | Ruled out - needs chain, sprocket and reduction design |

---

## Selection Rationale

**Why hub motor over mid-drive?**
- Simpler drivetrain - no chain, sprocket, or reduction gearbox to design/source
- Lower maintenance
- Direct fit into existing frame with 19" rim
- Tradeoff: more unsprung mass, less torque multiplication

**Why QS205 specifically?**
- 190 Nm max torque at the wheel with no reduction needed - adequate for enduro use per the [power/torque calc](../01-calculations/power-torque-at-wheel.md)
- The reference motor in the Surron/DIY e-moto community - wiring, tuning and Fardriver pairing all well documented
- Known-good pairing with the Fardriver ND72450 at 72 V
- 3.5T winding balances top speed (~55 mph predicted at 72 V) against launch torque
- 150 mm dropout matches the frame

---

## Key Specs (QS205 50H V3, 3.5T)

| Spec | Value |
|------|-------|
| Voltage | 72 V (48-96 V capable) |
| KV | ~12.9 RPM/V (derived from 5T datasheet 9.03 KV × 5/3.5 - verify by spin test) |
| Rated power | 3 kW |
| Peak power | ~5-6 kW |
| Max torque | 190 Nm |
| Magnet height | 50 mm ("50H") |
| Pole pairs | 16 (32 magnets) |
| Max efficiency | ~89% |
| Weight | ~14 kg |
| Dropout | 150 mm |

---

## Lessons

- Budget hub motors don't always match the spec sheet - measure dropout spacing before ordering (learned in Phase 0)
- Winding choice (T-count) is the real speed/torque decision on a hub motor - same motor, completely different character
