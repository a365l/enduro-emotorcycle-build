# Fardriver ND72450 — Parameter Reference

## Connector & Pin Reference

| Connector | Function | Wire colour |
|-----------|----------|-------------|
| High brake | Brake cut-off (high signal) | |
| Low brake | Brake cut-off (low signal) | |
| Ignition | Power on | |
| Hall connector | Motor hall sensors (A/B/C) | White/Green/Red (motor side) |
| Throttle | Throttle signal | |
| Three-speed | Speed limit select | Blue=slow, Black=mid, Yellow=high |
| Alarm & lock | Anti-theft motor lock | Red Deutsch connector |
| Analog meter | Speed/power meter output | |
| Program port | PC tuning software | |
| Velocity pulse | Speedometer output | |
| Reverse | Reverse enable | |
| Boost & cruise | Boost button / cruise control | |
| Bluetooth adapter | Wireless programming | |

---

## Fault Beep Codes

| Beeps | Fault | Action |
|-------|-------|--------|
| 1 | Motor hall fault | Check hall sensor connector and wiring |
| 2 | Throttle fail | Check throttle connector and signal voltage |
| 3 | Amp protect (overcurrent) | Check motor phase wires, reduce current limit |
| 4 | Phase current fault | Check phase wire connections |
| 5 | Voltage failure | Check battery voltage and main connections |
| 6 | Security lock active | Disable anti-theft lock |
| 7 | Motor overheated | Allow motor to cool |
| 8 | Controller overheated | Allow controller to cool, improve airflow |

---

## Autolearn Procedure

1. Connect motor phase wires and hall sensor
2. Power on controller
3. Listen for sequence: 2 short beeps, then B-E-E-P pattern
4. Autolearn completes: motor now mapped to controller
5. Test with gentle throttle before full power

> Autolearn must be repeated any time motor or controller is replaced.

---

## Phase Wire Connections

| Controller terminal | Motor phase | Colour |
|--------------------|-------------|--------|
| A | Phase A | Blue |
| B | Phase B | Green  |
| C | Phase C | Yellow |

> See `../phase-2-fardriver/IMG_5464.JPEG` for installed photo.

---

## Software Tuning Notes

| Tool | Platform | Use |
|------|----------|-----|
| Fardriver BT app | Android/iOS | Basic parameter read/write |
| Fardriver PC software | Windows | Full parameter access, data logging |

> Log all parameter changes in `../05-testing/fardriver-tuning/README.md`
