# Trade Study: Wiring Method - Crimping vs Soldering

## Decision

Phase 0/1: Soldered connections throughout  
Phase 2 onwards: **Crimped terminals** for all low-voltage signal wiring

---

## Comparison

| Property | Soldering | Crimping |
|----------|-----------|----------|
| Connection resistance | Very low (if done well) | Low (comparable) |
| Cold joint risk | Yes - failure mode with vibration | No |
| Vibration resistance | Poor without strain relief | Excellent |
| Serviceability | Requires soldering iron on-bike | Disconnect and re-crimp |
| Speed | Slower | Faster for harness work |
| Equipment needed | Iron, solder, flux, heat shrink | Crimping tool + terminals |
| Skill sensitivity | High - cold joints hard to detect | Lower - consistent with correct tool |
| Suitable for signal wiring | Yes | Yes (preferred) |
| Suitable for high-current (power cables) | Yes | Yes (hydraulic crimp for large AWG) |

---

## Decision Rationale

- Vehicle wiring is subject to constant vibration - cold solder joints fail over time
- All OEM vehicle wiring uses crimped terminals for exactly this reason
- The Fardriver signal harness uses Molex connectors natively - crimping matches the system
- Crimped joints are fully serviceable: pull the connector, replace the wire, re-crimp. No heat gun needed in the field
- The US PRO 101pc kit covers all signal wire gauges used in this build

---

## Tooling

| Tool | Use |
|------|-----|
| US PRO 101pc crimping kit (Item 6813) | Signal wire crimping (red/blue/yellow terminals) |
| [Hydraulic crimper if used] | Large AWG power cables |

---

## Lessons

- Map all wire assignments before crimping - pulling connectors apart to fix a wrong crimp wastes terminals and time (learned with Surron throttle to Fardriver adapter)
- Buy more terminals than you think you need
