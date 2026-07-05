# Product Design Spec - Enduro E-Motorcycle

Full DIY electric enduro conversion - donor ICE enduro frames with hub motor, lithium pack and Fardriver controller. Goal is a properly rideable trail bike, not just a proof of concept.

---

## Performance targets

Targets set from the [calculation set](../01-calculations/) - provisional until validated on the first instrumented ride.

| ID | Requirement | Target | Measured | Done |
|----|-------------|--------|----------|------|
| P-001 | Top speed (flat) | > 50 mph (predicted ~55) | | [ ] |
| P-002 | Range (trail) | > 15 km (predicted 17-25) | | [ ] |
| P-003 | 0-30 mph | < 4.5 s (predicted ~3.6) | | [ ] |
| P-004 | Max gradient | Climbs local trail hills without derate | | [ ] |
| P-005 | Kerb weight | < 80 kg (weigh at next teardown) | | [ ] |

---

## Electrical

| ID | Requirement | Target | Status |
|----|-------------|--------|--------|
| E-001 | Bus voltage | 72V | done |
| E-002 | Peak current | 450A | done - Fardriver ND72450 |
| E-003 | Continuous current | 200A | done |
| E-004 | Battery capacity | >= 2kWh | done - 2.16kWh |
| E-005 | Battery discharge rate | >= 100A | done - NBPower rated 100A |
| E-006 | All connections reworkable without soldering | Crimped | done from Phase 2 |

---

## Safety

| ID | Requirement | Status |
|----|-------------|--------|
| S-001 | Battery fused | [ ] |
| S-002 | Phase wire insulation rated for voltage | [ ] |
| S-003 | Controller has thermal protection | done - Fardriver has onboard cutout |
| S-004 | Brakes working before any powered run | done |
| S-005 | No exposed HV terminals | [ ] |

---

## Constraints

- Budget: ~£3,000+ across all phases (partially offset by donor-bike flipping - exact tally in the [BOMs](../04-bom/))
- Must use existing donor frame
- Off-road only

---

## Not doing (this build)

- Road registration
- ABS
- Regen braking (Fardriver supports it, just not configured yet)
