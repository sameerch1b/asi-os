# Decisions Log

Append-only record of meaningful decisions and why they were made. `/level-up` Phase 2 (Method interview) writes scoped automation specs here. You can also append manually whenever you decide something worth remembering.

**Format per entry:**

```
## YYYY-MM-DD — Short title

**Decision:** what was decided.

**Why:** the reasoning, constraints, and what would change your mind.

**Alternatives considered:** what else was on the table.

**Owner:** who's accountable.
```

Keep it terse. Future-you will thank present-you for capturing the *why*, not just the *what*.

---

## Grilled entries

Anything that went through `/grill` carries five extra lines. They're what make this log readable later instead of write-only:

```
**Grilled:** YYYY-MM-DD, SURVIVES | SURVIVES WITH CONDITIONS | DOES NOT SURVIVE

**Evidence:** N load-bearing claims: N observed, N sourced, N inferred

**Worse off:** who, and what they're likely to do about it

**Kill condition:** the specific, observable event that would reverse this

**Review:** YYYY-MM-DD

**Conditions:** numbered list with owners and dates, or "none"
```

The **kill condition** is the most valuable line in the file. It's what turns a decision from something you asserted once into something that can be scored later. It has to be observable by someone other than you. "If it stops feeling right" doesn't count, "if we're under 3 signed by 30 September" does.

Run `/grill --reckon` to sweep this file for kill conditions that have fired and review dates that have passed.

**Append-only.** Reversing an earlier decision means a new dated entry that references the old one. Never edit history. The whole point is being able to see what you thought at the time.

---
