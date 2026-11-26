# Interview Angles

Real problems from the build that I can talk about in interviews (L6 apprenticeships, Cambridge/Imperial). Only real problems go here, nothing forced. Each one needs evidence in the repo before I use it.

Status: **Live** = in progress, **Ready** = solved, retested and evidenced.

---

## #1 - Brake caliper clearance after the motor swap (Live) ⭐ first authentic angle

**Situation:** I upgraded to a QS205 hub motor. The same rotor, adapter and caliper had plenty of clearance on the old motor, but the QS205 hub is bigger and changed the geometry. The side of the adapter ended up ~0.5-1 mm from the rotor face, in line with the rotor's cut-outs, and the mount flexed under braking.

**Why it matters:** if the rotor or mount deflects, the adapter could catch a cut-out and lock the rear wheel.

**What I did / will do:**
- Found and measured the problem (gap, rotor wobble, flex before/after tightening)
- Found that loose bolts / low preload were part of the flex (tightening reduced play)
- Wrote requirements: ≥3 mm clearance both sides, no flex under braking, caliper centred, nothing protruding on the rotor side, fits the QS205
- Pugh matrix of options: solid rotor, bigger rotor, rounded adapter edges, bought bracket, custom bracket
- Interim risk reduction: rounded adapter edges / solid rotor change the failure from "catch and lock" to "rub" (lower severity)
- Hand calcs: braking force at the caliper, bolt load, bracket bending, preload
- CAD → 3D-printed test fit → milled part → retest against the requirements

**Skills it shows:** root-cause analysis, requirements, trade studies, risk / failure-mode thinking, hand calcs, CAD, prototyping, manufacture, test and verification.

**Evidence:** FL-005, FL-006 in `06-failure-log/`; photos 01, 66-76 in `logbook/session/media/26-11-21/`. To add: measurements, Pugh matrix (`02-trade-studies/`), calcs (`01-calculations/`), CAD, test results.

**Likely questions to prepare for:**
- Why not just buy a bigger rotor? (It moves the caliper outward but doesn't fix side clearance.)
- How did you know the flex was preload and not the spacers?
- How did you check your design worked?
- What would you do differently?

---

## Candidates (real, need evidence/retest before use)

- **Brake smoke diagnosis:** ruling out causes one variable at a time, plus audio spectrograms to separate a rub from motor whine → grease-contaminated pads (FL-004)
- **Dead-on-arrival controller caught with a 10-second continuity check** before it went near a 100 A pack (FL-002)
- **Controller bottleneck:** the 80 A controller was the limit, not the 100 A battery (FL-003)
- **Runaway throttle:** a safety issue, found, investigated and closed with evidence (FL-007, once solved)
- **DC-DC "dead" misdiagnosis:** checking units and probe contact before condemning a part (FL-010)
