# Failure Log

_Running record: symptom → root cause → fix → retest. Add entries as issues occur._

**Evidence standard:** a root cause is only marked **Confirmed** when it's backed by direct evidence - a measurement (meter reading, gauge, torque), a photo of the physical cause (witness marks, contamination, damage), or a repeatable test where changing one variable makes the fault come and go. Anything else is a **Hypothesis**, with the evidence for and against listed. AI suggestions are used to plan tests, never as evidence. Successful fixes are logged too, with the retest evidence.

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

## FL-004 - 21/11/2026 - Smoke from the rear brake on bench runs

**Phase:** 3

**Symptom:** Big plume of smoke from the rear wheel/caliper area after full-throttle no-load runs on the bench. Nothing felt hot afterwards and there were no scuff marks.

**Photo:** `../logbook/session/media/26-11-21/57-bench-run-2-smoke.mov`, `59-bench-run-2-smoke-frames.jpg`, `60-rotor-cable-clearance.jpg`

**Root cause:** Hypothesis (strong): grease from the rotor bolts contaminating the pads, burning off under braking.
- Evidence for: smoke on runs 1-2 when I braked the spinning wheel; run 3 with no braking = no smoke (video 61); heavy grease seen on the rotor bolts; brown streaky braking track (photo 60).
- Ruled out: motor cable rub (tied clear, no scuffs), strap/tyre rub (no marks).
- Still needed to confirm: photo of the pads out of the caliper (oil staining/glazing), and a no-smoke retest with new pads + degreased rotor.

**Fix:** Replace pads (metal/sintered), degrease rotor + bolts, check caliper/hose for leaks, blue Loctite (not grease) on rotor bolts, bed in.

**Retest result:** PENDING

**Lesson:** Isolate one variable per run. Spectrograms of phone audio helped separate a mechanical rub from normal motor whine.

---

## FL-005 - 21/11/2026 - Rear caliper flexing 1-2 mm

**Phase:** 3

**Symptom:** Caliper moved 1-2 mm under hard thumb pressure.

**Photo:** `../logbook/session/media/26-11-21/01-rear-caliper-on-10mm-standoffs.jpg`, `75-caliper-adapter-standoffs-side.jpg`

**Root cause:** Partly confirmed: one mount bolt was found not fully tight (tightening it visibly reduced the play). Hypothesis for the rest: and the bolts only thread into the Shimano adapter (no nut, short engagement) so they can't hold real preload. Two separate standoffs rock when the clamp load is low.

**Fix:** Tightened the loose bolt + washers (much less play). Next: proper 10.9 bolts with enough thread engagement or nyloc nuts, Loctite, torque wrench. If it still flexes, a one-piece milled bracket.

**Retest result:** Partially fixed - play much reduced, possible light catch under heavy braking. Marker witness test pending.

**Lesson:** Preload, not spacer geometry, was the main problem. Check every bolt in a load path before redesigning parts.

---

## FL-006 - 21/11/2026 - Rotor running ~1 mm from mount hardware

**Phase:** 3

**Symptom:** A mount bolt tip and the caliper mounting boss sit ~1 mm from the rotor - catches when the mount flexes under braking.

**Photo:** `../logbook/session/media/26-11-21/67-screw-to-rotor-gap-closeup.jpg`, `74-rotor-over-caliper-boss.jpg`

**Root cause:** Hypothesis (strong): the motor swap. The same rotor, adapter and caliper had plenty of clearance on the old hub motor. The QS205 hub is bigger and puts the rotor in a different position, so the old caliper geometry no longer fits (the 10 mm standoffs were a workaround for that). Plus through-bolts with tips pointing at the rotor. Evidence needed: rotor diameter, adapter code, hub shell diameter at the caliper, dropout-face-to-rotor-face distance, and where exactly the zero clearance is (rotor↔adapter or caliper↔hub).

**Fix:** Needs a custom solution for the QS205. Options: (1) a larger rotor + matching adapter to move the caliper radially outward away from the bigger hub (also improves braking capacity); (2) a QS205-specific brake bracket if one exists; (3) a custom axle-referenced caliper hanger designed around measured QS205 geometry, ≥3 mm clearance, blind tapped holes. Don't file the boss.

**Retest result:** PENDING

**Lesson:** Design clearance in, don't rely on parts "not quite touching" when static.

---

## FL-007 - 21/11/2026 - Runaway throttle

**Phase:** 3

**Symptom:** After a run the motor kept driving at ~half throttle with the throttle released. Only the key stopped it.

**Root cause:** Hypothesis, unconfirmed. Suspect 1: Fardriver Cruise Function engaged after a steady hold - normally cancelled by the brake, but my brake cut-offs aren't wired. Suspect 2: throttle signal fault (lost ground or signal shorted towards 5 V) in the adapter wiring.

**Fix:** Cruise OFF. Measure throttle signal at idle (~0.8-1.0 V expected). Wire brake cut-off switches. Fit a handlebar kill switch.

**Retest result:** PENDING - no running until resolved.

**Lesson:** Brake cut-offs and a kill switch should go in before the first powered test, not after.

---

## FL-008 - 21/11/2026 - Persistent hum with the wheel stopped

**Phase:** 3

**Symptom:** Motor/controller hummed for the whole 13 s clip with the wheel stationary (previously only a couple of seconds).

**Photo:** `../logbook/session/media/26-11-21/65-stationary-hum-spectrogram.png`

**Root cause:** Hypothesis: the controller is still driving current into a stopped motor.
- Evidence: wheel stopped by hand in the video but the hum continues; spectrogram of my recording shows steady tones (~4 / 7.3 / 10 kHz) for the whole clip.
- Still needed: Graph-tab screenshot of throttle voltage + phase current while it hums.
- Possibly the same cause as FL-007, or a hold/regen setting (Energy feedback was on 0-follow).

**Fix:** Check throttle V + phase current in the Graph tab while it hums. Try Cruise/P off and regen 1 (none).

**Retest result:** PENDING

**Lesson:** "Normal noises" need data before they're dismissed.

---

## FL-009 - 21/11/2026 - Thin-wire butt crimps pulling out

**Phase:** 3

**Symptom:** Five red butt crimps on thin signal wire pulled straight out.

**Photo:** `../logbook/session/media/26-11-21/48-failed-butt-crimps.jpg`

**Root cause:** Wire thinner than the terminal's range - under-filled barrel, nothing to grip. Stamped crimpers make it worse.

**Fix:** Fold strands back to bulk the wire before crimping. Buy a ratchet crimper.

**Retest result:** Holding under a firm pull. To redo/reinforce before road use.

**Lesson:** Match wire gauge to terminal size.

---

## FL-010 - 21/11/2026 - DC-DC converter misdiagnosed as shorted

**Phase:** 3

**Symptom:** Input-to-output read "0" - looked like a shorted switching transistor.

**Photo:** `../logbook/session/media/26-11-21/35-dc-dc-resistance-test.jpg`

**Root cause:** Measurement error - meter was on the MΩ range and solder-tipped leads gave poor contact. Real reading ~8-18 MΩ, different each way (diode behaviour) = healthy.

**Fix:** Scrape tips clean, read the units on the display, confirm with diode mode, then a fused no-load power test (expect 12-14 V).

**Retest result:** Resistance check passed. Powered test PENDING.

**Lesson:** Check the units and probe contact before condemning a part.

---
