# Session 02 - 21/11/26 - Brakes, Ignition & Smoke Diagnosis
- Phase 3. First logged session (see #01 for the unlogged work before this). First proper session in the new garage after the house move. Long one - roughly 14:00 to 19:40.

## What I did
- Checked the rear caliper - it flexed 1-2 mm by hand. Mounted on two separate 10 mm standoffs.
- Widened a frame hole with a carbide burr.
- Reviewed the battery box - controller heatsink was facing the pack.
- Traced the ignition key, tested it with continuity (simple 2-wire switch), labelled it.
- Stacked a second lug on controller B+ for an accessory feed, built a key-feed lead down to thin wire with a JST, continuity-checked it (0.39 Ω).
- Cut off the key plug and wired the key direct: feed → key → Fardriver Ignition, with the switched side Y-split to a spare ACC lead for lights.
- Identified the lights (headlight + Temu dual-colour bar). Traced the bar's maker from the CE label → car part → 12 V only.
- Tested the 72→12 V DC-DC for a shorted transistor. Thought it was dead, was actually a units misread (MΩ). Probably healthy.
- Notched the controller terminal cover so it seats over two leads.
- Strapped the rear up from a roof truss and did bench runs. Auto-learn passed.
- Smoke on two runs. Diagnosed with photos, frame grabs and spectrograms of the audio → smoke only when braking → grease-contaminated pads.
- Runaway throttle: motor kept driving at ~half throttle after release, only stopped with the key.
- Found a loose mount bolt (big part of the flex) and weak thread grip in the adapter. Fitted washers - much less play.
- Found the rotor runs within ~1 mm of the caliper mounting boss and a bolt tip.

## Decisions made
- Lights run from a 12 V DC-DC, never straight off 72 V. JST-SM fine on the 72 V input (~1 A), XT30 on the 12 V lamp side (~5 A).
- Fused distribution block for new circuits instead of stacking a third lug on B+.
- Caliper fix order: fix preload first (proper bolts, thread engagement, Loctite, torque), retest, then make a one-piece bracket if it still flexes.
- New bracket rule: blind tapped holes - nothing protrudes on the rotor side, ≥3 mm clearance everywhere.
- Mill it myself (simple 3-axis part). JLCCNC as a backup (~£25-60).
- No more bench runs until: new pads, degreased rotor, Cruise off, brake cut-offs wired, kill switch.

## Related files
- `wiring-key.md` - ignition circuit, label codes, 12 V plan
- `06-failure-log/failure-log.md` - FL-004 to FL-010 from today
- `logbook/session/media/26-11-21/` - all 76 photos, videos and spectrograms

## Blockers / open questions
- Runaway throttle - cruise setting or throttle wiring fault? Need Graph-tab data (throttle V + phase current) while it hums.
- Is the rotor centred in the caliper, and does the adapter match the rotor size?
- MT501 brakes are marginal for this bike's kinetic energy (~37 kJ at 80 km/h vs ~7 kJ MTB). Need a proper calc in `01-calculations/braking.md`.
- Measuring by ruler isn't accurate enough for CAD - need digital calipers.

## Next session
- New pads (metal/sintered), degrease rotor, find any leak, Loctite rotor bolts, bed in.
- Cruise OFF, P OFF, regen to 1 (none) → retest hum. Measure throttle signal at idle (expect ~0.8-1.0 V).
- Wire brake cut-off switches, fit a kill switch, fit a ≥72 V DC fuse in the key feed.
- Marker witness test on the mount under hard braking.
- Measure the mount properly and start the bracket CAD.

## Photo log
Every photo/video from the session, grouped by job.

### Brakes - first look

| # | File | What it shows |
|---|---|---|
| 01 | [01-rear-caliper-on-10mm-standoffs.jpg](media/26-11-21/01-rear-caliper-on-10mm-standoffs.jpg) | Rear Shimano 4-piston caliper on its post-mount adapter, lifted on two separate 10 mm standoffs. Moves 1-2 mm under hard thumb pressure - the start of the day's brake investigation. |
| 75 | [75-caliper-adapter-standoffs-side.jpg](media/26-11-21/75-caliper-adapter-standoffs-side.jpg) | Side view of the full stack: caliper → Shimano adapter → 10 mm standoffs → swingarm plate. Every interface here is a joint that can rock. |
| 76 | [76-caliper-adapter-standoffs-front.jpg](media/26-11-21/76-caliper-adapter-standoffs-front.jpg) | Front view of the same stack, used to explain the stack to my dad and plan the replacement bracket. |

### Frame and layout

| # | File | What it shows |
|---|---|---|
| 02 | [02-frame-hole-burr-dust.jpg](media/26-11-21/02-frame-hole-burr-dust.jpg) | Steel and paint dust from widening a frame hole with a carbide burr (7.94 × 19 × 6 mm), run dry in drill mode on high speed. Fine dust - mask, glasses, door open. |
| 03 | [03-battery-box-controller-layout.jpg](media/26-11-21/03-battery-box-controller-layout.jpg) | Battery box: NBPower 72 V pack, BMS and wiring. The Fardriver heatsink was facing the pack - heat going straight into the cells. Plan: flip it to the frame or mount it outside. |
| 04 | [04-qs205-cable-excess-length.jpg](media/26-11-21/04-qs205-cable-excess-length.jpg) | QS205 motor cable with excess length. Plan: loose ≥15 cm loop, snug ties, slack left for full suspension travel. |
| 37 | [37-garage-tool-search-controller-off-bike.jpg](media/26-11-21/37-garage-tool-search-controller-off-bike.jpg) | New garage after the house move - hunting for tools, controller off the bike. |

### Ignition - tracing and testing

| # | File | What it shows |
|---|---|---|
| 05 | [05-ignition-wiring-trace.jpg](media/26-11-21/05-ignition-wiring-trace.jpg) | Tracing the ignition: key barrel, the charger line's yellow blade fuse, 8 AWG mains. |
| 06 | [06-key-cable-to-white-plug.jpg](media/26-11-21/06-key-cable-to-white-plug.jpg) | Key barrel cable running to a white 3-pin plug. |
| 07 | [07-harness-bundle-near-key-cable.jpg](media/26-11-21/07-harness-bundle-near-key-cable.jpg) | Signal harness bundle routed alongside the key cable - had to separate what belonged to the key. |
| 38 | [38-fardriver-harness-map-printout.jpg](media/26-11-21/38-fardriver-harness-map-printout.jpg) | Fardriver connector map printout - used to find the Ignition input. Confirmed the controller only reads inputs, so lights need their own 12 V supply. |
| 08 | [08-multimeter-setup.jpg](media/26-11-21/08-multimeter-setup.jpg) | Multimeter set up: COM + V/Ω input, never the 10 A socket for this. |
| 09 | [09-key-plug-red-orange.jpg](media/26-11-21/09-key-plug-red-orange.jpg) | Key plug pinout: only 2 wires in a 3-pin housing - red (supply) and orange (switched). |
| 10 | [10-continuity-ol-baseline.jpg](media/26-11-21/10-continuity-ol-baseline.jpg) | Continuity baseline: OL with key off. Key on → continuity. Simple 2-wire switch, no polarity. |
| 36 | [36-labelling-tape.jpg](media/26-11-21/36-labelling-tape.jpg) | Tape used for flag labels. Green/yellow is UK earth colour, so used only as written flags, never as a colour code. |
| 11 | [11-ign-label-fitted.jpg](media/26-11-21/11-ign-label-fitted.jpg) | Key cable labelled IGN. |

### Accessory feed off B+

| # | File | What it shows |
|---|---|---|
| 12 | [12-controller-b-plus-two-lugs.jpg](media/26-11-21/12-controller-b-plus-two-lugs.jpg) | Adding a second lug to controller B+ to feed the key and future lights. |
| 13 | [13-nd72450-label-lug-stack.jpg](media/26-11-21/13-nd72450-label-lug-stack.jpg) | Controller label confirms ND72450 (200 A / 450 A) - matches the repo spec. |
| 14 | [14-lugs-swapped-main-underneath.jpg](media/26-11-21/14-lugs-swapped-main-underneath.jpg) | Restacked: main 8 AWG power lug against the terminal, accessory lug on top. High-current path gets the direct contact. |
| 15 | [15-b-plus-accessory-lead-fitted.jpg](media/26-11-21/15-b-plus-accessory-lead-fitted.jpg) | 10 AWG accessory lead fitted on B+. Unfused and live - bare end taped until a fuse goes in. |
| 39 | [39-b-plus-lead-and-xt-main-leads.jpg](media/26-11-21/39-b-plus-lead-and-xt-main-leads.jpg) | Accessory lead alongside the XT main battery leads. |
| 42 | [42-b-plus-lug-stack-in-frame.jpg](media/26-11-21/42-b-plus-lug-stack-in-frame.jpg) | B+ lug stack in the frame. Asked about a third lug - decided against it (thread engagement, cover fit); a fused distribution block is the better way to add circuits. |

### Reusing parts

| # | File | What it shows |
|---|---|---|
| 16 | [16-old-controller-harvest-box.jpg](media/26-11-21/16-old-controller-harvest-box.jpg) | Old Phase 1 controller - stripped for its key connector. |
| 17 | [17-old-controller-connector-harvest.jpg](media/26-11-21/17-old-controller-connector-harvest.jpg) | Cutting the mating key connector off the old loom with long tails. |

### Stepping down to thin wire

| # | File | What it shows |
|---|---|---|
| 18 | [18-thin-wire-vs-yellow-terminal.jpg](media/26-11-21/18-thin-wire-vs-yellow-terminal.jpg) | Thin signal wire next to the 10 AWG yellow terminal - far too small to crimp into it. This joint is also exactly where the fuse belongs. |
| 19 | [19-soldering-pigtail-setup.jpg](media/26-11-21/19-soldering-pigtail-setup.jpg) | Weller station set up to solder a thin pigtail into a red terminal. |
| 20 | [20-solder-joint-pigtail.jpg](media/26-11-21/20-solder-joint-pigtail.jpg) | Soldered pigtail. Note: repo standard is crimp-only for vibration - this is a temporary bench joint. |
| 21 | [21-pigtail-taped-inline-connector.jpg](media/26-11-21/21-pigtail-taped-inline-connector.jpg) | Joint taped (temporary) with an inline single-pin JST-SM on the blue lead. |
| 22 | [22-key-feed-lead-assembled.jpg](media/26-11-21/22-key-feed-lead-assembled.jpg) | Key-feed lead complete: B+ → 10 AWG → joint → thin blue → JST. |
| 23 | [23-continuity-b-plus-to-feed-0-39-ohm.jpg](media/26-11-21/23-continuity-b-plus-to-feed-0-39-ohm.jpg) | Continuity B+ terminal → end of feed: 0.39 Ω, basically just meter lead resistance. Battery unplugged throughout. |

### Key wired in

| # | File | What it shows |
|---|---|---|
| 24 | [24-key-cable-ign-label-in-frame.jpg](media/26-11-21/24-key-cable-ign-label-in-frame.jpg) | IGN-labelled key cable in the frame, ready to connect. |
| 25 | [25-key-plug-removed-direct-wiring.jpg](media/26-11-21/25-key-plug-removed-direct-wiring.jpg) | White key plug cut off - key wired direct. Removable points kept: the JST on the feed and the Fardriver Ignition plug. |
| 26 | [26-thin-wire-crimp-slipping.jpg](media/26-11-21/26-thin-wire-crimp-slipping.jpg) | Butt crimps on the thin wire kept pulling out. |
| 27 | [27-folding-strands-for-crimp.jpg](media/26-11-21/27-folding-strands-for-crimp.jpg) | Fix: folding the strands back to bulk them up so the barrel has something to grip. |
| 48 | [48-failed-butt-crimps.jpg](media/26-11-21/48-failed-butt-crimps.jpg) | Five failed red butt crimps - crushed barrels with nothing inside. Under-filled barrel on thin wire. |
| 44 | [44-key-orange-to-feed-jst-connector.jpg](media/26-11-21/44-key-orange-to-feed-jst-connector.jpg) | Key orange crimped to the blue feed through a single-pin JST-SM. |
| 46 | [46-jst-adaptor-lead.jpg](media/26-11-21/46-jst-adaptor-lead.jpg) | Home-made JST-to-JST adaptor lead. Black wire used on a + run - needs red tape so it isn't read as ground. |
| 45 | [45-key-circuit-wired-jst-chain.jpg](media/26-11-21/45-key-circuit-wired-jst-chain.jpg) | Key circuit wired: B+ feed → JST → key → Fardriver ignition. Switched output Y-split to a spare ACC lead for the lights. |
| 47 | [47-key-ignition-feed-routed.jpg](media/26-11-21/47-key-ignition-feed-routed.jpg) | Feed routed down the frame to the Fardriver harness. Spotted two loose ring terminals to secure before powering. |

### Lights and 12 V

| # | File | What it shows |
|---|---|---|
| 28 | [28-front-headlight-4-led.jpg](media/26-11-21/28-front-headlight-4-led.jpg) | Front 4-LED headlight - voltage unknown, treated as 12 V. |
| 43 | [43-headlight-3-wire-connector.jpg](media/26-11-21/43-headlight-3-wire-connector.jpg) | Headlight's 3-wire connector (red/black/green) - + / − / control. To be tested on 12 V. |
| 29 | [29-light-bar-temu.jpg](media/26-11-21/29-light-bar-temu.jpg) | Temu light bar. |
| 30 | [30-light-bar-dual-colour-leds.jpg](media/26-11-21/30-light-bar-dual-colour-leds.jpg) | 20-LED double row, each a dual-colour white/amber chip. |
| 40 | [40-light-bar-end-cap-screws.jpg](media/26-11-21/40-light-bar-end-cap-screws.jpg) | Opening the end cap. |
| 31 | [31-light-bar-end-cap-open-3-wires.jpg](media/26-11-21/31-light-bar-end-cap-open-3-wires.jpg) | 3 wires inside: black ground, red and white for the two colours. No driver board at this end. |
| 32 | [32-light-bar-ce-label-demu.jpg](media/26-11-21/32-light-bar-ce-label-demu.jpg) | CE label: Guangzhou Demu Car Products, batch DMWT110. A car part → 12/24 V. Never connect it to 72 V. |
| 41 | [41-light-bar-temu-order-thumbnail.jpg](media/26-11-21/41-light-bar-temu-order-thumbnail.jpg) | The original Temu listing thumbnail - listing removed, no spec available. |
| 33 | [33-handlebar-switch-pod.jpg](media/26-11-21/33-handlebar-switch-pod.jpg) | Handlebar pod: headlight, indicator rocker, horn. To map with continuity. Bar needs a relay; indicators need a 12 V flasher relay. |
| 34 | [34-dc-dc-72v-12v-converter.jpg](media/26-11-21/34-dc-dc-72v-12v-converter.jpg) | 72 V → 12 V DC-DC converter (red in, yellow out, 2× black ground). |
| 35 | [35-dc-dc-resistance-test.jpg](media/26-11-21/35-dc-dc-resistance-test.jpg) | Checking for a shorted switching transistor. First read looked like 0 Ω (dead) - turned out to be a megaohm range + probe contact misread. Actual: ~8-18 MΩ, direction-dependent = healthy. |

### Controller cover

| # | File | What it shows |
|---|---|---|
| 50 | [50-controller-cover-two-b-plus-leads.jpg](media/26-11-21/50-controller-cover-two-b-plus-leads.jpg) | With two leads on B+ the terminal cover wouldn't seat - forcing it would pinch a live cable. |
| 51 | [51-cover-notched-fits.jpg](media/26-11-21/51-cover-notched-fits.jpg) | Notched the B+ slot and smoothed the edges. Cover sits flat, leads loose in the slot. |

### Bench rig

| # | File | What it shows |
|---|---|---|
| 49 | [49-garage-roof-trusses.jpg](media/26-11-21/49-garage-roof-trusses.jpg) | Garage trusses. Strap from a bottom chord near a nail plate, never the diagonal bracing. |
| 52 | [52-ratchet-strap-setup.jpg](media/26-11-21/52-ratchet-strap-setup.jpg) | Ratchet strap - kept jamming. |
| 53 | [53-ratchet-strap-threaded.jpg](media/26-11-21/53-ratchet-strap-threaded.jpg) | Threaded through the spindle. It was threaded backwards at first (tail folding back on itself = the jam). |
| 54 | [54-ratchet-strap-hanging.jpg](media/26-11-21/54-ratchet-strap-hanging.jpg) | Hung from the truss, ready to lift the rear wheel. |

### Bench runs and the smoke

| # | File | What it shows |
|---|---|---|
| 55 | [55-bench-run-noise.mov](media/26-11-21/55-bench-run-noise.mov) | Run 1 audio/video. Auto-learn passed. Heard a rub; full-throttle no-load run ended in a plume of smoke. |
| 56 | [56-bench-run-noise-spectrogram.png](media/26-11-21/56-bench-run-noise-spectrogram.png) | Spectrogram of run 1: evenly spaced broadband ticks (~9/s) = once-per-revolution contact, separate from the normal rising motor whine. |
| 57 | [57-bench-run-2-smoke.mov](media/26-11-21/57-bench-run-2-smoke.mov) | Run 2 (63 s, sliders - not repeating that). Smoke again at the end. |
| 58 | [58-bench-run-2-spectrogram.png](media/26-11-21/58-bench-run-2-spectrogram.png) | Run 2 spectrogram: ~5 throttle bursts with coast-down chirps; smoke follows the longest/fastest burst. |
| 59 | [59-bench-run-2-smoke-frames.jpg](media/26-11-21/59-bench-run-2-smoke-frames.jpg) | Frames 51-60 s: haze around the hub/axle area right after the final burst. |
| 60 | [60-rotor-cable-clearance.jpg](media/26-11-21/60-rotor-cable-clearance.jpg) | Inspection: motor cable leaves the axle near the rotor arms; brown, streaky braking track. Cable was tied clear with no scuffs - ruled out. |
| 61 | [61-bench-run-3.mov](media/26-11-21/61-bench-run-3.mov) | Run 3, rider's view. |
| 62 | [62-bench-run-3-spectrogram.png](media/26-11-21/62-bench-run-3-spectrogram.png) | Run 3: smooth tones, no once-per-rev ticks, no smoke. Confirmed smoke only happens when braking → grease-contaminated pads. |

### Controller behaviour

| # | File | What it shows |
|---|---|---|
| 63 | [63-fardriver-energy-feedback-options.png](media/26-11-21/63-fardriver-energy-feedback-options.png) | Fardriver regen options: 0-follow, 1-none (无), 2-4 brake-triggered EABS, 5-7 throttle-release EABS. |
| 64 | [64-stationary-hum.mov](media/26-11-21/64-stationary-hum.mov) | Hum with the wheel stopped, lasting the whole clip. |
| 65 | [65-stationary-hum-spectrogram.png](media/26-11-21/65-stationary-hum-spectrogram.png) | Steady switching tones (~4, 7.3, 10 kHz) + 200-800 Hz hum with the wheel stationary = controller still driving current. Linked to the runaway throttle event. |

### Mount clearance and bolts

| # | File | What it shows |
|---|---|---|
| 66 | [66-caliper-stack-rotor-side.jpg](media/26-11-21/66-caliper-stack-rotor-side.jpg) | Stack from the rotor side. |
| 67 | [67-screw-to-rotor-gap-closeup.jpg](media/26-11-21/67-screw-to-rotor-gap-closeup.jpg) | Mount screw tip ~1 mm from the rotor. No nut - it only threads into the Shimano adapter. |
| 68 | [68-rotor-edge-near-mount.jpg](media/26-11-21/68-rotor-edge-near-mount.jpg) | Rotor edge passing close to the mount hardware. |
| 69 | [69-mount-bolts-axle-rotor.jpg](media/26-11-21/69-mount-bolts-axle-rotor.jpg) | Mount bolts, axle nut and torque washer next to the rotor. |
| 72 | [72-mount-stack-underside-view.jpg](media/26-11-21/72-mount-stack-underside-view.jpg) | Underside: two standoffs on the plate with a third bolt between them pointing at the rotor. |
| 70 | [70-measuring-mount-offset-1.jpg](media/26-11-21/70-measuring-mount-offset-1.jpg) | Measuring offsets with a tape for the new bracket. |
| 71 | [71-measuring-mount-offset-2.jpg](media/26-11-21/71-measuring-mount-offset-2.jpg) | Second measurement. Tape hook play and parallax make this ±1-2 mm - digital calipers needed. |
| 73 | [73-rotor-near-adapter-after-washers.jpg](media/26-11-21/73-rotor-near-adapter-after-washers.jpg) | After fitting washers (dad's suggestion): far less play. Rotor edge still looks almost touching the adapter area. |
| 74 | [74-rotor-over-caliper-boss.jpg](media/26-11-21/74-rotor-over-caliper-boss.jpg) | Rotor edge over the caliper mounting boss. The boss holds the caliper thread - can't be filed. Always this close (checked older photos). |
