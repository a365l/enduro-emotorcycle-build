# Phase 2 — QS205 Motor & Fardriver Controller

## Overview

Phase 2 was a major drivetrain upgrade. The budget generic hub motor and 80A generic controller from Phase 0 were replaced with a **QS Motor QS205** and a **Fardriver ND72450** (200A continuous / 450A peak). The NBPower 72V 30Ah 100A battery was carried over — it was always capable of more than the old controller allowed, so the same pack now actually gets to breathe.

A 19" × 80/100 rim was also fitted to match the QS205 motor. Wiring methodology changed completely this phase — everything crimped with proper terminals rather than soldered, which proved faster and more serviceable. The autolearn process was completed and wiring tested.

---

## Upgrade Summary

| | Phase 0 | Phase 2 |
|---|---|---|
| Motor | Budget generic hub motor | QS Motor QS205 |
| Controller | Generic sine wave — 72V **80A** (limited by controller) | Fardriver ND72450 — 72V **200A cont / 450A peak** |
| Battery | NBPower 72V 30Ah 100A | NBPower 72V 30Ah 100A (same pack, now fully utilised) |
| Rim | Original | 19" 80/100 |
| Wiring method | Soldered | Crimped |

> The battery was always rated 100A — it was the generic 80A controller that was the bottleneck in Phase 0. The Fardriver removes that ceiling entirely.

---

## New Parts

| Component | Spec |
|-----------|------|
| Motor | QS Motor QS205 |
| Controller | Fardriver ND72450 (72V, 200A cont / 450A peak) |
| Rim | 19" 80/100 spoke rim |
| Crimping kit | US PRO 101pc crimping tool & terminal set (Item 6813) |
| Fasteners | M3–M10 cap head allen bolts, aluminium standoff spacers |
| Brake fluid | Shimano mineral oil (MT501 bleed) |

---

## Fardriver Controller

The Fardriver arrived in its distinctive blue anodised aluminium housing. The harness is a significant step up from the generic controller — labelled Molex connectors for every function, a Bluetooth programming adapter, and a proper program port for PC tuning.

![Fardriver harness — connectors](./IMG_5414.JPEG)
*Fardriver signal harness fresh out of the box — high brake, throttle, hall, ignition, program port, boost/cruise all on labelled Molex connectors. Red Deutsch connector for the security lock*

![Fardriver harness — angle 2](./IMG_5415.JPEG)
*Other side of the harness showing the blue heat-shrink butt connector and remaining signal lines*

![Fardriver harness near new rim](./IMG_5437.JPEG)
*Harness held up next to the new 19" rim — Fardriver labelling visible on the wheel sticker*

![Controller out of box with phase wires](./IMG_5438.JPEG)
*Fardriver body with full harness out of packaging — phase wires (yellow/green/blue) and power cables visible alongside the signal bundle*

![Controller in foam — Bluetooth antenna](./IMG_5442.JPEG)
*Controller still in foam — Bluetooth programming adapter and harness connectors. Fardriver label on the blue cardboard box*

![Controller in foam — closer](./IMG_5443.JPEG)
*Closer shot of the Fardriver box label and harness layout before unpacking*

![Fardriver mounted on bike — phase connections](./IMG_5464.JPEG)
*Fardriver installed on the bike — blue anodised body bolted to the frame. Phase connection bolts clearly visible (blue, green, yellow for B/C/A phases). Battery cables (red/black) connected with XT connector*

![Fardriver mounted — full view](./IMG_5465.JPEG)
*Side view with Fardriver fitted — blue controller sits above the NBPower battery in the frame, gold forks and seat visible. Full wiring run behind*

---

## Wiring Reference

Both the physical harness diagram and the full circuit diagram were printed and used throughout the wiring session.

![Fardriver wiring diagram — front](./IMG_5432.JPEG)
*Printed Fardriver connector map — High brake, Ignition, Hall connector, Throttle, Three speed (blue-slow/black-mid/yellow-high), Alarm & lock, Analog meter, Low brake, Program port, Velocity pulse, Reverse, Boost & cruise*

![Fardriver wiring diagram — pin table](./IMG_5433.JPEG)
*Back of the wiring sheet — full pin assignment table with connector types for every function including Bluetooth adapter and anti-theft motor lock*

![Fardriver full circuit diagram](./IMG_5478.JPG)
*Complete Fardriver circuit diagram (ND series two-wheeler) — all 29 pins numbered with wire colours, connector photos, and peripheral connections*

![Fardriver fault / beep codes](./IMG_5470.PNG)
*Fardriver error beep code reference — motor hall fault (1 beep), throttle fail (2), amp protect (3), phase current (4), voltage failure (5), security lock (6), motor overheated (7), controller temp (8). Auto-learn sequence: 2 short beeps then b-e-e-p pattern*

---

## Throttle Wiring — Surron to Fardriver Adapter

The Surron thumb throttle has different wire assignments to the Fardriver's throttle input. A mapping table was worked out and documented before crimping the adapter.

![Throttle wire mapping notebook](./IMG_5458.JPEG)
*Handwritten wire mapping: Surron Throt (neg=Black, sig=Blue, 5V=Brown) → Middleman adapter → Fardriver (black, green, red). Hall sensor wiring also mapped above (White→Blue, Green→Brown, Red→Yellow)*

![Throttle wiring notes — full page](./IMG_5459.JPEG)
*Full notebook page showing the complete mapping table with all three columns confirmed*

---

## Switch to Crimping

Phase 0 and 1 used soldered connections throughout. Phase 2 switched to crimped terminals for all low-voltage signal wiring — faster, more reliable under vibration, and fully serviceable without a soldering iron.

![US PRO crimping kit](./IMG_5435.JPEG)
*US PRO 101pc crimping tool & terminal set — the switch from soldering to crimping happened this phase. Red, blue, and yellow terminals for different wire gauges*

![Indoor wiring station](./IMG_5447.JPG)
*Moved indoors for the Fardriver wiring prep — cutting mat, harness laid out, crimp kit open, wiring diagrams to hand*

![Wiring session overview](./IMG_5453.JPG)
*Desk setup mid-session — Fardriver body top right, full harness being worked through, US PRO crimper ready*

![Connector prep on cutting mat](./IMG_5445.JPEG)
*Crimping a signal connector — harness connector held with wiring diagram visible for reference*

![Throttle connector wires](./IMG_5461.JPEG)
*Throttle connector wires cut and stripped on the cutting mat — red, blue, and white wires prepped for crimping into the Fardriver harness connector*

![Crimping in progress](./IMG_5460.JPEG)
*Connector being seated into the crimping tool — Fardriver body in background*

![Test leads wired up](./IMG_5462.JPEG)
*Test lead alligator clips wired into connectors for wiring verification before final fitment*

![eBay parts ordered](./IMG_5436.PNG)
*eBay orders for this phase — brake fluid for MT501 bleed, M3–M10 allen bolts, aluminium standoff spacers for controller mounting*

---

## Ceiling Rig — Back Again

![Ceiling rig anchor point](./IMG_5463.JPEG)
*The ceiling rig ratchet strap anchor point — blue strap looped over a roof joist. QS205 rear wheel visible on the floor behind the suspended bike. Same rig as Phase 0, still earning its keep*

---

## Autolearn & Wiring Test

With the Fardriver installed and all connections crimped, the autolearn process was completed. Autolearn initialises the controller to the motor's specific Hall sensor positions and phase timing — essential when pairing a Fardriver to any motor for the first time. Wiring was verified against the fault beep codes before any load testing.

---

## Video Documentation

| File | Description |
|------|-------------|
| `0C72DFE8-8445-487B-9072-40B329C2CA59.mp4` | Build / test footage |
| `4AFB221C-D29C-4A2C-9491-9B6AE3BE9F24.MP4` | Build / test footage |
| `78A89213-7881-4EBD-82A0-97392147DEA9.mp4` | Build / test footage |
| `845A2EF9-CC89-48CF-8BE8-EC29886458C5.mp4` | Build / test footage |
| `9F43726C-A141-433B-B117-AFAAB4BD7C71.mp4` | Build / test footage |
| `A44CBB71-0E12-4F58-9C1A-7BD41321CC49.MP4` | Build / test footage |
| `B92F1C23-7964-4C15-BF32-A9986A1F499F-1.MP4` | Build / test footage |
| `B92F1C23-7964-4C15-BF32-A9986A1F499F.MP4` | Build / test footage |
| `D6489E8D-0688-4015-8BC9-E88D88AAB6FA.MP4` | Build / test footage |
| `FEB6DE88-A585-4C64-9A17-73551434D5D0.MP4` | Build / test footage |
| `IMG_5442.MOV` | Controller unboxing |
| `IMG_5443.MOV` | Controller unboxing |
| `IMG_5445.MOV` | Crimping session |
| `IMG_5446.MOV` | Crimping session |
| `IMG_5454.MOV` | Wiring notes |
| `IMG_5455.MOV` | Wiring session |
| `IMG_5458.MOV` | Throttle mapping |
| `IMG_5459.MOV` | Throttle mapping |
| `IMG_5460.MOV` | Connector crimping |
| `IMG_5461.MOV` | Connector crimping |
| `IMG_5462.MOV` | Test wiring |
| `IMG_5463.MOV` | Ceiling rig / install |
| `IMG_5464.MOV` | Fardriver install |
| `IMG_5465.MOV` | Fardriver install |
| `IMG_5466.MP4` | Autolearn / test |
| `IMG_5467.MP4` | Autolearn / test |
| `IMG_5468.MP4` | Autolearn / test |
| `IMG_5469.MP4` | Autolearn / test |

> Fill in video descriptions after review

---

## Lessons & Notes

- Crimping is better than soldering for signal wiring in a vehicle — no cold joints, no heat damage to insulation, and every connection can be remade without a soldering iron
- The Surron throttle signal wiring does not match the Fardriver throttle input pin-for-pin — map it before crimping anything, or you'll pull connectors apart
- Fardriver autolearn must be done every time the motor or controller is swapped — skipping it causes the motor to run rough or not at all
- The fault beep codes are genuinely useful for diagnosing issues without a laptop — worth memorising the first three (hall fault, throttle fail, amp protect)
- The NBPower 100A pack was always the right battery — the Phase 0 generic controller was the limiting factor the whole time
