# Wiring Key

Reference for every circuit on the bike: what each wire does, where it goes, how it's protected and what its label says. Update this whenever a wire is added, moved or relabelled.

**System:** 72 V NBPower pack (100 A BMS) → Fardriver ND72450 → QS205 3.5T hub motor

---

## Label codes

Flag labels on the wires (Sharpie on tape, heat-shrink labels in the final build).

| Label | Circuit | Status |
|---|---|---|
| `IGN` | Key switch cable (red/orange) | Fitted 2026-11-21 |
| `B+ KEY` | Fused B+ feed to the key switch | To fit |
| `CHG` | Charger port feed | To fit |
| `HALL` | QS205 hall/temp sensor plug | To fit |

> Green/yellow tape is the UK earth colour code. Use it for written flag labels only, never as a colour code on a live wire.

---

## Circuits

### 1. Main power (battery → controller)

| From | To | Wire | Protection | Notes |
|---|---|---|---|---|
| Battery + (BMS out) | Controller B+ | 8 AWG red, 200 °C silicone | BMS | XT connector |
| Battery − | Controller B− | 8 AWG black, 200 °C silicone | BMS | XT connector |

Always live while the battery is connected. The key does **not** switch this.

### 2. Ignition (key switch)

```
Controller B+ ──[FUSE 3–5 A]──red── KEY SWITCH ──orange── Controller IGNITION
                                    (closes when key ON)
```

| Wire | Function | Connects to |
|---|---|---|
| Red | Supply in, at pack voltage | Controller B+, **through a fuse** |
| Orange | Switched out, at pack voltage with the key ON | Controller ignition connector (check the Fardriver pin sheet) |

*As wired 2026-11-21: key **orange** ↔ B+ feed (10 AWG → pigtail → inline connector) and key **red** ↔ Fardriver ignition (orange). The switch has no polarity, so this is equivalent. A spare `ACC 72V SW` lead is planned to feed or enable the DC-DC.*

- **Key connector:** white 3-pin housing with 2 positions used (red and orange) and 1 empty slot.
- **Switch type:** simple 2-wire contact with no polarity. Continuity tested on 2026-11-21: OL with the key off, continuous with the key on.
- **Fuse:** 3–5 A, **rated ≥ 72 V DC**. A ceramic 5×20 mm 250 V fuse in an inline holder works. A standard 32 V car blade fuse is not suitable. ⚠️ *Not yet fitted. Bench testing only until it is.*
- **Terminal at B+:** ring terminal under the B+ bolt, heat-shrunk.

**Verification test (to do):** set the meter to V⎓ with the black probe on B−.

| Point | Key OFF | Key ON |
|---|---|---|
| Orange at the controller ignition pin | 0 V | 72–84 V (pack voltage) |

### 3. Charger

| From | To | Protection | Notes |
|---|---|---|---|
| Charge port | Battery | Inline yellow blade fuse | ⚠️ Blade fuse is likely a 32 V part. Replace with one rated ≥ 72 V DC. |

### 4. Motor (QS205 → controller)

| Wire | Function | Notes |
|---|---|---|
| Yellow / green / blue (thick) | Phases A / C / B | Ring-lug terminals. Insulate exposed lugs with boots or heat-shrink. |
| Hall + temp (thin, in the same sheath) | Rotor position and motor temperature | Insulation chafed by the rotor near the axle. Repair with self-amalgamating tape, then reroute away from the rotor. |

**Excess cable length:** store as a loose loop (≥ 15–20 cm diameter), ties snug but not crushing. Keep slack for full suspension travel.

### 5. 12V accessories (planned)

```
ACC 72V SW ──[fuse]── DC-DC 72V→12V ──[12V fuses]── switch pod / relays ── lights, indicators, horn
B− ACC ───────────── DC-DC ground (common)
```

| Item | Notes |
|---|---|
| DC-DC | Red = 72V in, yellow = 12V out, black ×2 = common ground. Unit 1 passed the resistance check. Unit 2 untested. |
| Light bar | Temu dual-colour white/amber, 20 LEDs, maker Guangzhou Demu Car Products (car part). **12V only.** 3 wires: black = ground, red/white = the colours. Draw TBC. Switch via a relay. |
| Headlight | 4-LED, voltage unknown. Run at 12V. |
| Switch pod | Headlight, indicator rocker (common + L + R), horn. Indicators need a 12V LED flasher relay. |

### 6. Signal harness (Fardriver)

See the [connector map](./phase-2-fardriver/README.md#wiring-reference) and [`07-firmware-config/fardriver-parameters.md`](./07-firmware-config/fardriver-parameters.md) for the full pin table: high/low brake, ignition, hall, throttle, three-speed, alarm and lock, analog meter, program port, reverse, boost/cruise.

---

## Open issues

| Issue | Action |
|---|---|
| Ignition feed is unfused | Fit a 3–5 A fuse rated ≥ 72 V DC at the B+ end |
| Charger fuse voltage rating | Replace with a fuse rated ≥ 72 V DC |
| Hall cable chafe at the rotor | Repair and reroute |
| Exposed phase ring lugs | Insulate |
| Controller heatsink faces the battery | Flip it to face the frame, or mount it outside the box. Monitor temperature in the Fardriver app (target < 70 °C). |
