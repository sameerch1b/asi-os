# The Grill: the decision pressure test

> *The Grill is original to ASI OS. Built by ASI Intelligence (asiintelligence.io).*

> *"Speed times a wrong call is just a bigger mistake, delivered sooner."*

---

## Why this exists

An AIOS makes you faster. Faster is only good if the calls are right.

Here is the failure mode nobody warns you about. As your AIOS gets better, it gets more agreeable. It has read your context files. It knows your priorities. It knows how you write. So it starts finishing your sentences, and the thing that finishes your sentences is not the thing that catches your mistakes. You end up with a very fast, very well-informed yes-man.

The Grill is the counterweight. It is an adversarial interview you run on a decision **before** you commit to it, and before it goes in the log.

**The one rule that makes it work: the Grill has to find something.** A Grill that comes back "looks good to me" has failed, not passed. If five stands produce no weakness, the interview was too soft. Run it again harder.

---

## Where it sits in the kit

| Skill | Question it answers | Domain |
|---|---|---|
| `/audit` | Is the AIOS built right? | Form |
| `/level-up` | What leverage am I missing? | Function |
| `/grill` | Should I do this at all, and how would I know if I was wrong? | Judgment |

`/audit` and `/level-up` make you productive. `/grill` stops you being productive in the wrong direction.

It runs at three moments:

1. **Before a real decision.** Pricing, hiring, a build-versus-buy, a client you are unsure about, a strategic bet.
2. **Inside `/level-up` Phase 2.** Before an automation spec gets written to the log, the spec itself gets grilled.
3. **On the log, looking backwards.** The reckoning. See below.

---

## The Five Stands

A decision has to survive five stands. Each one attacks from a different angle, because decisions do not fail in one way. Run them in order. Later stands depend on earlier answers.

### Stand 1: EVIDENCE

*What do you actually know, and what are you just carrying?*

Pull out every claim the decision leans on. Sort each one into a tier:

| Tier | Meaning |
|---|---|
| **Observed** | You saw it. In a system, in a document, with a date on it. |
| **Sourced** | A named third party said it and you can point at where. |
| **Inferred** | You reasoned it from something Observed or Sourced. The reasoning is stated. |
| **Assumed** | You believe it. No basis given. |

Then ask one question per claim: **is this load-bearing?** Load-bearing means the decision changes if the claim is false.

**Hard stop: any claim that is both load-bearing and Assumed ends the Grill.** Not a warning. A stop. Two ways out. Go and get the evidence, or restate the decision so it no longer depends on that claim.

This is the stand that catches the most, because most bad decisions are not bad reasoning. They are good reasoning on top of a number nobody checked.

### Stand 2: REVERSAL

*Argue the other side, properly.*

Build the strongest available case **against** the decision. Not a strawman you can knock over. The version a smart person who disagrees with you would actually make.

If the case against comes out weak in your hands, that is not evidence the case is weak. That is evidence you have not understood it yet. Go back and build it again.

**Rule: you have to name the condition under which the opposite choice is correct.** "There isn't one" is not an answer. Every real decision has a world where the other branch wins. Describe that world. Then say how far you are from it.

### Stand 3: COST

*Price the null option.*

Most decisions get compared against a fantasy. They should be compared against doing nothing.

- What does the status quo cost over the same horizon, in the same units?
- What does this decision make **harder** later? Second-order effects.
- What does it commit you to that you cannot easily undo?
- What does it take off the table? Every yes is a no to something.

**Rule: if doing nothing costs less than doing it, and you still want to do it, say the non-financial reason out loud.** Sometimes that reason is completely valid: strategic positioning, a relationship, optionality, learning. It just has to be spoken, not smuggled.

### Stand 4: COUNTERPARTY

*Whose incentive runs against yours.*

Any decision that touches another person has a second agenda in the room. Client, partner, contractor, supplier, regulator, a competitor, and your own future self at 11pm under deadline pressure.

- Who is worse off if this goes ahead?
- What will they do about it, realistically?
- Who has to agree to this who has not been asked?
- Where does this decision assume goodwill that has not been tested?

**Rule: name at least one party who is worse off, and one concrete thing they might do.** "Everybody wins" is almost never true, and when it is genuinely true you should be able to explain why the usual tension is absent.

### Stand 5: KILL

*Pre-register the reversal.*

Before you commit, write down what would make you undo it.

- What specific, **observable** event would make you reverse this call?
- By what date, or past what threshold?
- Who is watching for it?

**Rule: if nothing would change your mind, this is a belief, not a decision.** Beliefs are allowed. They just do not go in the decisions log, because the log exists to be checked and a belief cannot be checked.

The kill condition is the single most valuable line in the whole log. It converts a decision from a thing you asserted once into a thing that can be scored later.

---

## The verdict

Three outcomes only. No fourth, no hedge.

| Verdict | Meaning |
|---|---|
| **SURVIVES** | All five stands cleared. Kill condition registered. Go. |
| **SURVIVES WITH CONDITIONS** | Cleared, but named conditions have to be true. Conditions are written into the log with owners. |
| **DOES NOT SURVIVE** | A stand failed. The specific stand and the specific reason are named. |

`DOES NOT SURVIVE` is a good outcome. It is cheaper here than in the market.

---

## The Reckoning

This is the part that compounds, and the reason the Grill is worth more in month six than in week one.

Most decision logs are write-only. People record what they decided and never read it again. So the same mistake gets made twice, eighteen months apart, by the same person, who has genuinely forgotten.

Because every grilled decision carries a **kill condition** and a **review date**, the log becomes readable. `/grill --reckon` sweeps `decisions/log.md` and pulls back anything where:

- the kill condition has fired,
- the review date has passed,
- or a condition attached to a `SURVIVES WITH CONDITIONS` verdict was never confirmed.

Each one goes back on the table with a straight question: *this fired, what now?*

Over a year this produces something no audit score can: a record of your own judgment with the outcomes attached. You find out which of your instincts are good and which ones you should stop trusting. That is the actual endgame of a personal operating system. Not automation. Calibration.

---

## The anti-sycophancy rules

These are what stop the Grill degrading into agreement over time. They are not style preferences. Drop them and the skill is worthless.

1. **Never open with agreement.** No "great question", no "solid plan". Open on the first stand.
2. **Never grade your own homework.** If the decision came out of `/level-up`, or the AIOS suggested it, the Grill argues against it harder, not softer.
3. **One question at a time.** Wait for the answer. A wall of questions gets a wall of shallow answers.
4. **Do not accept the first answer on Evidence.** The first answer is always the confident one. Ask where the number came from.
5. **Look it up rather than ask.** If a fact is sitting in `context/`, `connections.md`, or the log, go and read it. Spend the user's attention on judgment, not on retrieval.
6. **No hedged verdict.** Three outcomes. Pick one.
7. **Finding nothing is a failed run, not a pass.** Say so, and go again.

---

## Running it well

- **Grill decisions, not tasks.** "Should we take this client" is a decision. "Reply to this email" is a task. The Grill is expensive attention. Spend it on things that are hard to reverse.
- **Grill before you are committed, not after.** Once you have told someone, the Grill turns into justification. The output is worthless.
- **Bring the decision, not the conclusion.** If you arrive with the answer and want it validated, say so up front, and expect Stand 2 to hurt.
- **Fifteen to twenty five minutes.** If it is running longer, the decision is really two decisions. Split it.

---

## What it produces

Every completed run writes one entry to `decisions/log.md` carrying:

- the decision, in one sentence
- the evidence tiers for load-bearing claims
- the strongest case against, and the condition under which it wins
- the null-option cost
- the counterparty who is worse off
- the kill condition and review date
- the verdict, and any conditions with owners

That entry is what `--reckon` reads later. It is also the single best artifact to hand a partner, a board, or your future self, because it shows the reasoning and not just the outcome.

---

> *The Grill is original to ASI OS. Built by ASI Intelligence (asiintelligence.io).*
