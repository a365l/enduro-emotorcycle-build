# Trade Study: Battery Selection

## Decision

Retained: **NBPower 72V 30Ah 100A** (carried from Phase 0 through Phase 2)

---

## Rationale for Retaining Phase 0 Pack

The NBPower pack was always rated 100A — the Phase 0 generic 80A controller was the limiting factor, not the battery. With the Fardriver installed, the pack now operates within its design envelope.

> Key insight: the battery was never the bottleneck. Replacing it in Phase 2 would have been unnecessary spend.

---

## Options Considered for Future Upgrade

| Option | Chemistry | Voltage | Capacity | Peak discharge | Energy | Cost | Notes |
|--------|-----------|---------|----------|---------------|--------|------|-------|
| NBPower 72V 30Ah (current) | [Li-ion / LiFePO4?] | 72V | 30Ah | 100A | 2.16kWh | £[X] | Retained |
| [Higher capacity pack] | | 72V | 40–50Ah | | | | More range |
| [LiFePO4 upgrade] | LiFePO4 | 72V | 30Ah | | 2.16kWh | £[X] | Better cycle life, safer chemistry |
| DIY pack | 21700 cells | 72V | [X]Ah | [X]A | [X]kWh | £[X] | Custom size/shape |

---

## Chemistry Comparison

| Property | NMC (Li-ion) | LiFePO4 |
|----------|-------------|----------|
| Energy density (Wh/kg) | ~200 | ~120–140 |
| Cycle life | ~500–1000 | ~2000–3000 |
| Thermal stability | Lower | Higher (safer) |
| Cost per Wh | Lower | Higher |
| Nominal cell voltage | 3.6V | 3.2V |

> If replacing the pack in a future phase, LiFePO4 is worth considering for the safety and cycle life benefits, at the cost of lower energy density (larger/heavier pack for same capacity).

---

## Key Specs (Current Pack)

| Spec | Value |
|------|-------|
| Nominal voltage | 72V |
| Capacity | 30Ah |
| Energy | 2.16kWh |
| Max discharge current | 100A |
| Chemistry | [Check label / datasheet] |
| BMS included | [Yes / No] |
| Connector type | [XT90 / Anderson / other] |
