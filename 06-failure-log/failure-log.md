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

## FL-002 — [Date] — [Title]

**Phase:**

**Symptom:**

**Photo:**

**Root cause:**

**Fix:**

**Retest result:**

**Lesson:**

---

## FL-003 — [Date] — [Title]

**Phase:**

**Symptom:**

**Photo:**

**Root cause:**

**Fix:**

**Retest result:**

**Lesson:**

---
