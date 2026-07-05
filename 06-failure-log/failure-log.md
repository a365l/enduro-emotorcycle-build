# Failure Log

_Running record: symptom → root cause → fix → retest. Add entries as issues occur._

---

## FL-001 — [Date] — Throttle wiring mismatch: Surron → Fardriver

**Phase:** 2

**Symptom:** Throttle connector from Surron thumb throttle did not match Fardriver throttle input pin assignments. Could not connect directly.

**Photo:** `../phase-2-fardriver/IMG_5458.JPEG` (handwritten mapping)

**Root cause:** Surron throttle uses different wire colour assignments to Fardriver signal harness. No standard across manufacturers.

| Signal | Surron wire | Fardriver pin |
|--------|-------------|---------------|
| GND | Black | Black |
| Signal | Blue | Green |
| 5V | Brown | Red |

**Fix:** Mapped wire assignments before crimping. Built a middleman adapter using crimped terminals.

**Retest result:** Throttle functional after adapter. No issues.

**Lesson:** Always map wire assignments before crimping. Pulling connectors apart wastes terminals and time.

---

## FL-002 — Phase 1 — Sabvaton controller dead on arrival

**Phase:** 1

**Symptom:** Continuity between B+ and B- battery terminals on a secondhand Sabvaton controller, found on the bench before it was ever connected to the bike. A dead short across the DC bus.

**Photo:** `../phase-1-donor-bikes-and-repairs/IMG_0801.JPEG` (trial-fitted before the fault was confirmed)

**Root cause:** Shorted MOSFETs - a common failure on this class of controller, usually from a gate-driver fault or previous over-voltage event.

**Fix:** MOSFET replacement attempted. Identifying which of the 18-24 FETs failed requires checking each gate-to-drain individually; the repair didn't get past this stage. Controller written off. Sourced a Fardriver ND72450 instead.

**Retest result:** N/A - written off. Fardriver installed in Phase 2 and verified working.

**Lesson:** Continuity-check B+ to B- on any secondhand controller before connecting anything. It costs nothing and takes 10 seconds with a multimeter - here it prevented connecting a dead short across a 100 A pack.

---

## FL-003 — Phase 0-2 — 80 A controller bottlenecked a 100 A battery

**Phase:** 0 (discovered), 2 (resolved)

**Symptom:** Underwhelming acceleration and hill performance through the whole of Phase 0, despite a healthy 72 V 30 Ah 100 A pack.

**Root cause:** The generic Phase 0 controller was rated 80 A - the pack could deliver 100 A but was never asked for it. The battery was assumed to be the weak link; it was the controller the entire time.

**Fix:** Replaced with a Fardriver ND72450 (200 A continuous / 450 A peak) in Phase 2. The pack is now the sustained limit, which is the correct hierarchy for this build.

**Retest result:** Bench-verified on the rig (autolearn complete, wiring checked against fault codes). Performance delta to be quantified on the first instrumented ride - see [test vs prediction](../05-testing/test-vs-prediction.md).

**Lesson:** Identify the limiting component with numbers, not assumptions - every element of the powertrain has a current rating, and the system is only as strong as the lowest one.

---
