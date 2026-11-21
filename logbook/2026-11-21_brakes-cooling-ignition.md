# Session Log — 21 Nov 2026

## What was done

Workshop session after the house move. Checked brake caliper rigidity, widened a frame hole, reviewed controller cooling and motor cable routing, then traced and tested the ignition key circuit. Everything was photographed for the build write-up.

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
- **Thin-wire crimps slipping:** the wire is too thin for red terminals. Fold the strands back to bulk them up. Longer term, get a ratchet crimper.
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

## Next session plan

1. Buy fuses rated ≥ 72 V DC (3–5 A ceramic 5×20 mm plus an inline holder) and self-amalgamating tape
2. Wire the ignition and run the voltage test (see [wiring key](../wiring-key.md))
3. Repair and reroute the hall cable
4. Flip or relocate the controller and log its temperatures on a test run
5. Mill the caliper spacer block

## Time spent

[X] hours
