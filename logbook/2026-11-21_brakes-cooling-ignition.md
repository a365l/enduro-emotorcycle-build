# Session Log — 21 Nov 2026

## What was done

Workshop session after the house move. Checked brake caliper rigidity, widened a frame hole, reviewed controller cooling and motor cable routing, then traced and tested the ignition key circuit. Everything was photographed for the build write-up.

## Build story (in order)

1. **Brakes:** found the rear Shimano caliper flexing 1–2 mm under thumb pressure. It sat on two separate 10 mm standoffs. A rotor spacer was ruled out (the rotor already sits close to the hall cable and has chewed it), so the plan is a one-piece milled spacer block. (01)
2. **Frame:** widened a frame hole with a carbide burr, run dry; mask and glasses for the steel/paint dust. (02)
3. **Cooling:** the Fardriver's heatsink was facing the battery pack, so the plan is to flip it toward the frame or move it outside the box. (03)
4. **Motor cable:** planned the QS205 cable's excess length as a loose loop with slack for suspension travel. (04)
5. **Ignition, tracing:** traced the key barrel to a white 3-pin plug with only 2 wires (red/orange). Continuity: OL key off, continuous key on, so a simple switch with no polarity. Labelled it `IGN`. (05–11)
6. **Accessory feed off B+:** stacked a second 10 AWG lug on controller B+, swapped so the main 8 AWG lug sits against the terminal. Confirmed the controller is an ND72450 (200/450 A). (12–15, 39)
7. **Parts reuse:** harvested the mating key connector from the old Phase 1 controller's loom. (16–17)
8. **Step-down to thin wire:** the thin wire was too small for the yellow terminal, so I soldered a pigtail into a red terminal, taped it, and added an inline single-pin JST-SM. Continuity B+ → feed end: 0.39 Ω. (18–23)
9. **Key wired direct:** cut the key plug off. Key orange → B+ feed via JST, key red → Fardriver ignition. Doubled two wires in one crimp to Y-split the switched output into ignition and a spare accessory lead for the lights. (24–25, 44–47)
10. **Crimping lesson:** 5 butt crimps failed on thin wire because the barrel was under-filled. Fixed by folding the strands back to bulk them up. A ratchet crimper is on the shopping list. (26–27, 48)
11. **Lights:** identified a 4-LED headlight (3-wire: +, −, control) and a Temu dual-colour 20-LED bar. The CE label traced the maker to Guangzhou Demu Car Products (a car part), so it's 12V only. Mapped the 3-wire bar (black ground, red/white colours). (28–32, 40–41, 43)
12. **Power for the lights:** the 72V→12V DC-DC converter read MΩ input→output with different readings each way (diode behaviour), so it's probably healthy. An earlier "0 Ω" was a probe-contact and units mix-up. Worked out that the 72V input side draws only ~1A, so JST-SM is fine there, but the 12V side to the 60W bar is ~5A and needs an XT30. (34–35)
13. **Switch pod:** headlight / indicators / horn pod to map with continuity. Indicators need a flasher relay, and the bar should go through a relay. (33)
14. **Workshop:** checked the garage roof trusses for strapping the bike up: use a bottom chord near a nail plate, never the diagonal bracing. (49)
15. **Terminal cover:** with two leads on B+, the controller cover wouldn't seat. Notched the B+ slot and smoothed the edges, and it now sits flat with the leads loose in the slot. Never force a lid onto live cables. (50–51)
16. **Rear lift:** set up a ratchet strap from a roof truss to lift the rear wheel for bench testing. Learned the anti-jam method: pull the slack through by hand first, keep to 1½–2 wraps on the spindle, and release fully flat. (52–54)
17. **First powered bench run:** rear lifted on the strap; Fardriver auto-learn completed fine. A rub was audible. On a full-throttle no-load run, a large plume of smoke came from the caliper/rear wheel area. Stopped testing. Suspects: rotor cutting into the already-chafed hall/phase cable, or pads dragging on the rotor (caliper on flexy standoffs). Investigation pending. Nothing was hot afterwards, which points to brief friction (strap or tyre rub) rather than pad drag. Also found a caliper-mount screw pointing at the rotor with under 1 mm static clearance: a likely contact point once the rotor and the flexy caliper move at speed.
18. **Noise analysis:** recorded the bench run and generated a spectrogram (ffmpeg). It shows regularly spaced broadband ticks (~9 per second at low speed), consistent with something contacting once per wheel revolution, separate from the normal rising FOC/motor whine. Supports the rub hypothesis. (55–56)
19. **Second bench run:** smoke again, appearing just after the longest/fastest throttle burst. Under investigation: pad/rotor contamination (possibly brake fluid from the earlier bleed) heating up when braking a fast-spinning wheel, vs rotor contact with the mount screw. Inspection (60) found the thick motor cable leaving the axle and running right against the rotor's inner arms (the same cable already chewed before), plus a thin black strip/tie tail next to it, and a brown, discoloured braking track. The cable was found firmly tied clear with no scuff marks anywhere, so a rub is unlikely. **New prime suspect: grease.** Heavy grease on the rotor bolts gets flung outward at high RPM onto the rotor and pads, then burns off. That fits the sudden smoke, nothing staying hot, no scuffs, and the brown streaky braking track. (57–60)
20. **Third bench run:** the audio shows smooth motor tones with no periodic ticking (unlike run 1), and no visible smoke in the frames. (61–62)
21. **Root cause confirmed:** smoke happens **only when braking**, never under power. Diagnosis: contaminated pads (grease from the rotor bolts, possibly mineral oil from the bleed) burning off when braking a fast-spinning wheel. Fix: degrease the rotor, replace the pads, check the caliper/hose for leaks, bed in the new pads, and threadlock (not grease) the rotor bolts.
22. **⚠️ Runaway throttle:** after a run, the motor kept driving at about half throttle with the throttle released, and only stopped when the key was turned off. Suspect #1: Fardriver **Cruise function** enabled (it engages after a steady hold and cancels only via the brake input, and the brake cut-off switches aren't wired). Suspect #2: a throttle signal fault (lost ground, or the signal shorted toward 5V). Actions: disable cruise, wire the brake cut-offs, measure the throttle signal at idle, fit a kill switch. No running until resolved.
23. **Persistent stationary hum:** the post-throttle buzz now lasted the whole 13 s clip with the wheel stopped. The audio shows steady switching tones, so the controller is still driving current, not a mechanical noise. Likely linked to step 22 (a throttle signal not returning to idle, or cruise/hold/EABS). Next: watch throttle voltage + phase current in the Graph tab while it hums. (64–65)
24. **Mount screw / rotor clearance:** a loose mount screw was found and tightened, which greatly reduced the caliper play, so the loose bolt was a big part of the original 1–2 mm flex. Under heavy braking the stack still flexes enough for the screw tip (~1 mm from the rotor) to catch it. Design rule for the new bracket: **blind tapped holes, so no bolt protrudes on the rotor side**, with ≥3 mm rotor clearance. (66–69)
25. **Weak bolt grip:** the mount screws came out very easily despite being tightened hard, which points to short thread engagement and/or worn or stripped threads in a thin plate, plus no threadlocker. Actions: check engagement, re-tap or Helicoil any stripped holes (or through-bolt with nyloc nuts), and use blue Loctite at a measured torque.
26. **Washers fitted (dad's suggestion):** the caliper play is much reduced. The rotor edge now looks almost in contact with the adapter / lower caliper bolt area. To confirm: paper/drill-bit gap gauge plus marker witness test, and check whether the washers shifted the stack toward the rotor. Past photos confirm the rotor was always this close to the caliper mounting boss (74). The boss holds the caliper thread, so filing is ruled out. After tightening, it runs fine, with a possible light catch only under heavy braking. Next: rotor centring check, adapter/rotor size check, marker witness test. New bracket to design in ≥3 mm clearance.

## Progress

- [x] Rear caliper flex check: the caliper moves 1–2 mm under hard thumb pressure. The Shimano post-mount adapter sits on two separate 10 mm standoffs.
- [x] Frame hole widened with a carbide burr (7.94 × 19 × 6 mm cylindrical), run dry in drill mode on high speed
- [x] Controller cooling review: the heatsink was facing the battery pack
- [x] QS205 cable excess: plan to store it as a loose loop with slack for suspension travel
- [x] Ignition key traced to a white 3-pin plug with 2 wires (red/orange)
- [x] Key continuity test passed: a simple switch with no polarity
- [x] Key cable labelled `IGN`
- [x] Second lug (10 AWG) stacked on controller B+ for the ignition/accessory feed, with the main 8 AWG lug against the terminal
- [x] Key-feed lead built: 10 AWG off B+ → soldered thin-wire pigtail (taped temporarily) → inline single-pin connector
- [x] Continuity B+ → end of the key feed: 0.39 Ω (≈ meter lead resistance)
- [x] Key plug cut off. Key wired direct: key red ↔ Fardriver ignition (orange), key orange ↔ B+ feed. The switch has no polarity.
- [x] Lights identified: 4-LED headlight, plus a Temu dual-colour (white/amber) 20-LED bar made by Guangzhou Demu Car Products. No voltage rating on it, so it's treated as 12V.
- [x] 72V→12V DC-DC: input→output read in MΩ, different in each direction (diode behaviour), so probably healthy
- [ ] Fit a fuse rated ≥ 72V DC in the key feed (blade fuse only for supervised bench tests)
- [ ] Voltage test at the ignition pin
- [ ] DC-DC: diode-mode check, then fused no-load test (expect 12–14V on yellow). Test unit 2.
- [ ] Light bar on the 12V jump pack: check which wire is white/amber and measure current draw
- [ ] Map the switch pod with continuity
- [ ] Mill a one-piece caliper spacer block

## What worked

- Continuity test confirmed the key switch quickly
- Standard ebike key convention held: red = supply, orange = switched output

## What didn't work / issues found

- **Caliper mount:** two separate standoffs on bolts bend under braking load. The fix is a single milled spacer block, because a rotor spacer isn't possible (rotor already sits close to the hall cable).
- **Hall cable chafe:** the rotor has already chewed the hall/motor cable insulation
- **Controller heatsink facing the battery:** it heats the pack. Flip it to face the frame or move it outside the box.
- **No fuses on hand:** the ignition feed must be fused before riding
- **Charger blade fuse** is probably 32 V rated on a 72 V system
- **Thin-wire crimps slipping (5 failed butt crimps, photo 48):** the wire is too thin for red terminals. Fold the strands back to bulk them up. Longer term, get a ratchet crimper.
- **DC-DC misread:** the meter was on the MΩ range, so "8"/"18" were megaohms (healthy), not ohms. Check the units on the display.

## Measurements / data taken

| Measurement | Value |
|---|---|
| Caliper standoff height | ~10 mm |
| Caliper deflection (hard thumb pressure) | ~1–2 mm |
| Key switch, key OFF (red–orange) | OL (open) |
| Key switch, key ON (red–orange) | Continuity |
| B+ terminal → key-feed end | 0.39 Ω |
| DC-DC red (in) → yellow (out) | ~8–18 MΩ, direction-dependent |

## Caliper spacer block spec (to make)

- 6082/6061 aluminium or mild steel, 10 mm thick (measure the existing standoffs exactly)
- One piece spanning both adapter bolt holes, about 8 mm of material past each hole, 20–25 mm wide
- Faces milled flat and parallel. Holes positioned from the actual adapter.
- Grade 10.9 bolts, about 10 mm longer, Loctite 243, torqued properly

## Photos

| # | Photo |
|---|---|
| 01 | ![Caliper on standoffs](./2026-11-21-photos/01-rear-caliper-on-10mm-standoffs.jpg) Rear Shimano caliper on its post-mount adapter, lifted on two 10 mm standoffs |
| 02 | ![Burr dust](./2026-11-21-photos/02-frame-hole-burr-dust.jpg) Steel/paint dust from widening the frame hole with a carbide burr |
| 03 | ![Battery box](./2026-11-21-photos/03-battery-box-controller-layout.jpg) Battery box layout: NBPower pack, BMS and wiring |
| 04 | ![QS205 cable](./2026-11-21-photos/04-qs205-cable-excess-length.jpg) QS205 motor cable with excess length to manage |
| 05 | ![Ignition trace](./2026-11-21-photos/05-ignition-wiring-trace.jpg) Tracing the ignition wiring: key barrel, fused charger feed, 8 AWG mains |
| 06 | ![Key plug](./2026-11-21-photos/06-key-cable-to-white-plug.jpg) Key barrel cable running to the white 3-pin plug |
| 07 | ![Harness bundle](./2026-11-21-photos/07-harness-bundle-near-key-cable.jpg) Signal harness bundle routed alongside the key cable |
| 08 | ![Multimeter](./2026-11-21-photos/08-multimeter-setup.jpg) Multimeter setup: COM and V/Ω/continuity input |
| 09 | ![Red/orange](./2026-11-21-photos/09-key-plug-red-orange.jpg) Key plug pinout: red (supply) and orange (switched), one empty slot |
| 10 | ![OL baseline](./2026-11-21-photos/10-continuity-ol-baseline.jpg) Continuity test baseline: OL |
| 11 | ![IGN label](./2026-11-21-photos/11-ign-label-fitted.jpg) Key cable labelled `IGN` |
| 12 | ![Second lug added to controller B+](./2026-11-21-photos/12-controller-b-plus-two-lugs.jpg) Second lug added to controller B+ |
| 13 | ![ND72450 label (200 A / 450 A) and lug stacking](./2026-11-21-photos/13-nd72450-label-lug-stack.jpg) ND72450 label (200 A / 450 A) and lug stacking |
| 14 | ![Main power lug restacked against the terminal](./2026-11-21-photos/14-lugs-swapped-main-underneath.jpg) Main power lug restacked against the terminal |
| 15 | ![10 AWG accessory lead on B+](./2026-11-21-photos/15-b-plus-accessory-lead-fitted.jpg) 10 AWG accessory lead on B+ |
| 16 | ![Old Phase 1 controller, harvested for parts](./2026-11-21-photos/16-old-controller-harvest-box.jpg) Old Phase 1 controller, harvested for parts |
| 17 | ![Taking the mating key connector from the old loom](./2026-11-21-photos/17-old-controller-connector-harvest.jpg) Taking the mating key connector from the old loom |
| 18 | ![Thin wire vs 10 AWG yellow terminal: size mismatch](./2026-11-21-photos/18-thin-wire-vs-yellow-terminal.jpg) Thin wire vs 10 AWG yellow terminal: size mismatch |
| 19 | ![Soldering setup](./2026-11-21-photos/19-soldering-pigtail-setup.jpg) Soldering setup |
| 20 | ![Soldered thin-wire pigtail](./2026-11-21-photos/20-solder-joint-pigtail.jpg) Soldered thin-wire pigtail |
| 21 | ![Pigtail taped, with inline single-pin connector](./2026-11-21-photos/21-pigtail-taped-inline-connector.jpg) Pigtail taped, with inline single-pin connector |
| 22 | ![Key-feed lead assembled](./2026-11-21-photos/22-key-feed-lead-assembled.jpg) Key-feed lead assembled |
| 23 | ![Continuity check: 0.39 Ω](./2026-11-21-photos/23-continuity-b-plus-to-feed-0-39-ohm.jpg) Continuity check: 0.39 Ω |
| 24 | ![IGN-labelled key cable in the frame](./2026-11-21-photos/24-key-cable-ign-label-in-frame.jpg) IGN-labelled key cable in the frame |
| 25 | ![Key plug removed for direct wiring](./2026-11-21-photos/25-key-plug-removed-direct-wiring.jpg) Key plug removed for direct wiring |
| 26 | ![Thin-wire butt crimps slipping](./2026-11-21-photos/26-thin-wire-crimp-slipping.jpg) Thin-wire butt crimps slipping |
| 27 | ![Folding strands to bulk up the crimp](./2026-11-21-photos/27-folding-strands-for-crimp.jpg) Folding strands to bulk up the crimp |
| 28 | ![Front 4-LED headlight](./2026-11-21-photos/28-front-headlight-4-led.jpg) Front 4-LED headlight |
| 29 | ![Temu light bar](./2026-11-21-photos/29-light-bar-temu.jpg) Temu light bar |
| 30 | ![Dual-colour 20-LED double-row bar](./2026-11-21-photos/30-light-bar-dual-colour-leds.jpg) Dual-colour 20-LED double-row bar |
| 31 | ![End cap open: red/white/black, 3-wire dual colour](./2026-11-21-photos/31-light-bar-end-cap-open-3-wires.jpg) End cap open: red/white/black, 3-wire dual colour |
| 32 | ![CE label: Guangzhou Demu Car Products, batch DMWT110](./2026-11-21-photos/32-light-bar-ce-label-demu.jpg) CE label: Guangzhou Demu Car Products, batch DMWT110 |
| 33 | ![Handlebar switch pod: headlight, indicators, horn](./2026-11-21-photos/33-handlebar-switch-pod.jpg) Handlebar switch pod: headlight, indicators, horn |
| 34 | ![72V→12V DC-DC converter](./2026-11-21-photos/34-dc-dc-72v-12v-converter.jpg) 72V→12V DC-DC converter |
| 35 | ![DC-DC resistance test](./2026-11-21-photos/35-dc-dc-resistance-test.jpg) DC-DC resistance test |
| 36 | ![Labelling tape](./2026-11-21-photos/36-labelling-tape.jpg) Labelling tape |
| 37 | ![Garage after the move, controller off the bike](./2026-11-21-photos/37-garage-tool-search-controller-off-bike.jpg) Garage after the move, controller off the bike |
| 38 | ![Fardriver harness map printout](./2026-11-21-photos/38-fardriver-harness-map-printout.jpg) Fardriver harness map printout |
| 39 | ![B+ accessory lead and XT main leads](./2026-11-21-photos/39-b-plus-lead-and-xt-main-leads.jpg) B+ accessory lead and XT main leads |
| 40 | ![Light bar end cap screws](./2026-11-21-photos/40-light-bar-end-cap-screws.jpg) Light bar end cap screws |
| 41 | ![Temu order thumbnail](./2026-11-21-photos/41-light-bar-temu-order-thumbnail.jpg) Temu order thumbnail |
| 42 | ![B+ lug stack in the frame](./2026-11-21-photos/42-b-plus-lug-stack-in-frame.jpg) B+ lug stack in the frame |
| 43 | ![Headlight connector](./2026-11-21-photos/43-headlight-3-wire-connector.jpg) Headlight 3-wire connector (red/black/green) |
| 44 | ![Key feed connector](./2026-11-21-photos/44-key-orange-to-feed-jst-connector.jpg) Key orange crimped to the blue feed with a single-pin JST-SM connector |
| 45 | ![Key circuit wired](./2026-11-21-photos/45-key-circuit-wired-jst-chain.jpg) Key circuit wired: B+ feed → JST → key → Fardriver ignition |
| 46 | ![JST adaptor](./2026-11-21-photos/46-jst-adaptor-lead.jpg) Home-made JST-SM adaptor lead for the accessory feed |
| 47 | ![Feed routed](./2026-11-21-photos/47-key-ignition-feed-routed.jpg) Key/ignition feed routed down the frame to the Fardriver harness |
| 48 | ![Failed crimps](./2026-11-21-photos/48-failed-butt-crimps.jpg) 5 failed red butt crimps on thin wire, before switching to folded strands |
| 49 | ![Roof trusses](./2026-11-21-photos/49-garage-roof-trusses.jpg) Garage roof trusses: strap from a bottom chord near a nail plate, never the bracing |
| 50 | ![Cover](./2026-11-21-photos/50-controller-cover-two-b-plus-leads.jpg) Terminal cover won't seat with two B+ leads in one slot |
| 51 | ![Cover notched](./2026-11-21-photos/51-cover-notched-fits.jpg) B+ slot notched: cover now sits flat with both leads loose in the slot |
| 52 | ![Ratchet strap](./2026-11-21-photos/52-ratchet-strap-setup.jpg) Ratchet strap setup for lifting the rear off the ground |
| 53 | ![Strap threaded](./2026-11-21-photos/53-ratchet-strap-threaded.jpg) Strap threaded through the ratchet spindle |
| 54 | ![Strap hanging](./2026-11-21-photos/54-ratchet-strap-hanging.jpg) Strap hung from the truss, ready to lift the rear |
| 55 | [Video](./2026-11-21-photos/55-bench-run-noise.mov) Bench run noise recording (9 s) |
| 56 | ![Spectrogram](./2026-11-21-photos/56-bench-run-noise-spectrogram.png) Spectrogram of the bench-run audio: regular broadband ticks at ~9 Hz early on (a once-per-revolution contact), then rising tonal whine as the motor speeds up |
| 57 | [Video](./2026-11-21-photos/57-bench-run-2-smoke.mov) Second bench run (63 s): smoke at the end |
| 58 | ![Spectrogram](./2026-11-21-photos/58-bench-run-2-spectrogram.png) Spectrogram: about five throttle bursts with coast-down chirps; smoke follows the longest, fastest burst (~45–55 s) |
| 59 | ![Smoke frames](./2026-11-21-photos/59-bench-run-2-smoke-frames.jpg) Frames 51–60 s: haze appears around the upper hub/axle area right after the final burst |
| 60 | ![Rotor and cable](./2026-11-21-photos/60-rotor-cable-clearance.jpg) Post-run inspection: motor cable loops out of the axle right against the rotor's inner arms; brown/discoloured braking track |
| 61 | [Video](./2026-11-21-photos/61-bench-run-3.mov) Third bench run (53 s), rider's-eye view |
| 62 | ![Spectrogram](./2026-11-21-photos/62-bench-run-3-spectrogram.png) Spectrogram: smooth rising/falling motor tones, no once-per-rev ticking, extra broadband noise only at higher speed |
| 63 | ![EABS options](./2026-11-21-photos/63-fardriver-energy-feedback-options.png) Fardriver Energy feedback (regen) options: 0-follow, 1-none, 2–4 brake-triggered EABS, 5–7 throttle-release EABS |
| 64 | [Video](./2026-11-21-photos/64-stationary-hum.mov) Persistent hum with the wheel stationary (13 s) |
| 65 | ![Spectrogram](./2026-11-21-photos/65-stationary-hum-spectrogram.png) Spectrogram: constant tonal lines (~4, 7.3, 10 kHz) plus a 200–800 Hz hum throughout, with the wheel stopped, so the controller is still driving current into a stalled motor |
| 66 | ![Stack](./2026-11-21-photos/66-caliper-stack-rotor-side.jpg) Caliper mount stack from the rotor side |
| 67 | ![Gap](./2026-11-21-photos/67-screw-to-rotor-gap-closeup.jpg) Mount screw within ~1 mm of the rotor |
| 68 | ![Rotor edge](./2026-11-21-photos/68-rotor-edge-near-mount.jpg) Rotor edge passing close to the mount hardware |
| 69 | ![Bolts](./2026-11-21-photos/69-mount-bolts-axle-rotor.jpg) Mount bolts, axle nut and torque washer next to the rotor |
| 70 | ![Measuring 1](./2026-11-21-photos/70-measuring-mount-offset-1.jpg) Measuring the caliper/rotor to mount-plate offset with a tape |
| 71 | ![Measuring 2](./2026-11-21-photos/71-measuring-mount-offset-2.jpg) Second offset measurement |
| 72 | ![Underside](./2026-11-21-photos/72-mount-stack-underside-view.jpg) Underside view of the mount stack: two silver standoffs on the grey plate under the caliper, with a third bolt between them pointing up toward the rotor/caliper |
| 73 | ![Rotor near adapter](./2026-11-21-photos/73-rotor-near-adapter-after-washers.jpg) After fitting washers (dad's fix): play much reduced, but the rotor edge appears almost touching the adapter/caliper bolt area. Check the gap with a paper or drill-bit gauge |
| 74 | ![Rotor over boss](./2026-11-21-photos/74-rotor-over-caliper-boss.jpg) Rotor edge passing over the caliper mounting boss (threaded, so must NOT be filed) |
| 75 | ![Stack side](./2026-11-21-photos/75-caliper-adapter-standoffs-side.jpg) Caliper, Shimano adapter, 10 mm standoffs and plate: side view |
| 76 | ![Stack front](./2026-11-21-photos/76-caliper-adapter-standoffs-front.jpg) Same stack, front view |

## Next session plan

1. Buy fuses rated ≥ 72 V DC (3–5 A ceramic 5×20 mm plus an inline holder) and self-amalgamating tape
2. Wire the ignition and run the voltage test (see [wiring key](../wiring-key.md))
3. Repair and reroute the hall cable
4. Flip or relocate the controller and log its temperatures on a test run
5. Mill the caliper spacer block

## Time spent

[X] hours
