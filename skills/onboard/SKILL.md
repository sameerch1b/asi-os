---
name: onboard
description: Use on Day 1 of an ASI OS install, when someone says "set me up", "onboard me", "let's get started", "fill in my AIOS", has just cloned the kit, or has just installed the asi-os plugin. Combined wizard — builds the kit's folder structure if it isn't there yet, runs the 7-question intake, then scaffolds the Day-1 file set at the end. Idempotent — re-run any time after editing asi-os-intake.md.
---

## What this skill does

Single combined wizard. Reads or writes `asi-os-intake.md` (the canonical intake), conducts the 7-question interview if the file isn't filled, then scaffolds the Day-1 file set inline at the end of the run. No separate `/scaffold-from-intake` skill — this is one flow.

**The wow moment:** at the end, suggest the closing prompt *"Try this — ask me: what should I focus on this week?"* The user runs it once. That's the wow. There's no `/today` skill to save — the prompt itself plants the Mindset framework (Default Shift) for them to internalize.

## When NOT to run this

- If the user has already onboarded and wants to refresh: still run, but skip questions already answered (idempotent).
- If the user wants to add a new connection: that's not onboarding — point them at `connections.md` to edit directly, or schedule a `/level-up` Phase 2 walk.

## Execution

### Step 0: Scaffold the kit if it isn't here yet

ASI OS installs two ways, and this step is what makes the plugin path work.

- **Clone mode.** The user cloned the repo, so every folder and file already exists. Nothing to do here.
- **Plugin mode.** The user ran `/plugin install asi-os@asi` and is sitting in some arbitrary folder with none of the kit's files. The skills exist; the structure does not. **You build it.**

Detect by checking for `asi-os-intake.md` in the current working directory.

**If it exists → clone mode. Skip to Step 1.**

**If it does not exist → plugin mode.** Confirm the location before writing anything:

> *"I'll set your AIOS up in `{cwd}`. That folder becomes your operating system: your context, your connections, your decisions log. Right place, or somewhere else?"*

Wait for the answer. Never scaffold into a folder without confirming, and never scaffold into a directory that already holds an unrelated project unless the user says to.

Once confirmed, create:

```
context/          (empty, filled in Step 3)
references/
decisions/
archives/
```

Then write these four, copying from the plugin's own directory (`${CLAUDE_PLUGIN_ROOT}`) so the user gets their own editable copies:

| File | Source |
|---|---|
| `asi-os-intake.md` | `${CLAUDE_PLUGIN_ROOT}/asi-os-intake.md`, blank template |
| `connections.md` | `${CLAUDE_PLUGIN_ROOT}/connections.md`, blank 7-row table |
| `decisions/log.md` | `${CLAUDE_PLUGIN_ROOT}/decisions/log.md`, format header only |
| `CLAUDE.md` | `${CLAUDE_PLUGIN_ROOT}/CLAUDE.md`, `{{placeholders}}` intact, filled in Step 3 |
| `references/3ms-framework.md` | `${CLAUDE_PLUGIN_ROOT}/references/3ms-framework.md`, verbatim including its attribution block |
| `references/the-grill.md` | `${CLAUDE_PLUGIN_ROOT}/references/the-grill.md`, verbatim |

**Copy the two reference files, do not rewrite or summarise them.** `/level-up` and `/grill` both read them from `references/` at runtime, and `3ms-framework.md` carries Nate Herk's copyright and trademark notices that must travel with the content.

**If `${CLAUDE_PLUGIN_ROOT}` is not set or the source files can't be read,** say so plainly and point the user at the clone path rather than reconstructing the files from memory:

> *"I can't reach the plugin's files to copy them across. Quickest fix: `git clone https://github.com/sameerch1b/asi-os.git`, open that folder, and run `/onboard` again."*

Then say one line and continue straight into Step 1. Do not make the user re-invoke anything:

> *"Kit's in place. Seven questions, about fifteen minutes, and you can edit any answer later."*

### Step 1: Read the intake

Read `asi-os-intake.md`. Check which Q1-Q7 sections have content vs. `[Your answer here]` placeholders.

- **All filled** → skip Step 2, jump to Step 3 (scaffold).
- **Some filled** → ask the user: "I see Q1, Q3, Q4 are answered. Want to fill the rest now, or scaffold from what's there?" Their call.
- **None filled (fresh clone or fresh plugin scaffold)** → run Step 2 conversationally.

### Step 2: The interview (7 questions, hard cap)

Ask one at a time. Write each answer into `asi-os-intake.md` as you go (so the user can resume if interrupted).

**Q1 — Who are you, what do you sell, who do you sell it to?**
Identity, offer, ICP. One paragraph each is fine.

**Q2 — Paste 1-2 things you've written recently. Don't edit them.**
*This is the only question with a hard rule.* Voice samples MUST be pasted, not typed mid-conversation. If the user starts typing fresh prose, refuse:

> *"Stop — paste it raw. If you type it here while we're talking, the sample is already shaped by our conversation. Open your last email or LinkedIn post in another tab and paste the unedited text. This is the one rule I can't bend."*

Ask for two samples. One email, one post. Or two of either.

**Q3 — What are your 2-3 biggest priorities for the next 90 days?**
Quarterly priorities. Push back if they say "grow my business" — make them name a number, a deadline, or a deliverable.

**Q4 — Where does revenue actually land, and where is it tracked?**
Multiple answers OK. Map to Tier-1 Domain 1 (Revenue/Financials).

**Q5 — Where do you talk to customers, your team, and the outside world day-to-day?**
Email (Gmail/Outlook), Slack/Teams/Discord, DMs. Map to Domains 2 + 4.

**Q6 — Where do meeting recordings, notes, and important docs live?**
Map to Domains 6 + 7.

**Q7 — What's the one task that eats your week, and where do you currently track work?**
Capture top_pain (used by `/level-up` Day-14) + Domain 5 (tasks).

Domain 3 (Calendar) is auto-inferred from Q5: Gmail → Google Cal; Outlook → Outlook Cal. Confirm in Step 3.

### Step 3: Scaffold the Day-1 file set

Once the intake is complete, generate these files (or update if re-running). Back up originals to `archives/intake-{YYYY-MM-DD-HHMM}/` if any exist.

1. **`context/about-me.md`** — from Q1 (identity, role) + Q7 (top_pain). One short paragraph each.
2. **`context/about-business.md`** — from Q1 (offer, ICP) + Q4 (revenue model). One paragraph.
3. **`context/priorities.md`** — from Q3. Numbered list, one line per priority.
4. **`references/voice.md`** — from Q2. Paste samples verbatim with a short header explaining their use ("Match this register when drafting; don't fake voice on external content without showing me first").
5. **`connections.md`** — populate the 7-row table from Q4-Q7 answers. Each row gets `mechanism: not yet connected`, `auth: —`, `last checked: —`. The user wires connections on Day 2.
6. **`CLAUDE.md`** — fill all `{{...}}` placeholders. Substitute the user's name, stated priority, voice register summary, and a brief connections summary.

### Step 4: The closing screen

Print one screen. Four lines max:

```
✓ Day 1 done. Your AIOS knows who you are, what you sell, what matters this quarter, and how you sound.

Today: ask me — "what should I focus on this week?"
Tomorrow: pick one tool from connections.md and wire it up (manual MCP install or write a small API script + save references/{tool}-api.md).
Day 7: run /audit to see your score.
Any hard call, any time: run /grill before you commit. It's the one skill here that argues with you.
```

The `/grill` line is not optional. It is the skill people get the most out of and the one they are least likely to discover on their own, because nobody goes looking for something that disagrees with them.

When the user runs the closing prompt ("what should I focus on this week?"), respond using only the new context files. Hit:
- 3-bullet priority list, in their voice register from Q2
- Each bullet ties back to a stated 90-day priority from Q3
- Final line: *"If I had to pick one thing for Monday, it'd be [X], because [reason from priorities]. Want me to draft the first email? And — where could the Default Shift apply here? To what extent could AI be leveraged on this task?"*

The Default Shift question seeds the Mindset framework before `/level-up` formally introduces it on Day 14.

## Critical implementation rules

1. **The 7-question cap is non-negotiable.** Don't add Q8 in conversation.
2. **Voice paste cannot be skipped.** If the user types samples mid-chat, refuse and tell them to paste from real writing.
3. **One-shot scaffold.** After Step 2 ends, write Step 3 files in a single batch. No multi-turn confirmation. The user iterates by editing `asi-os-intake.md` and re-running.
4. **Idempotent.** Re-running with an edited intake refreshes context files; backs up originals to `archives/intake-{ts}/`. Skips questions already answered unless the user wants to revise.
5. **Closing screen is four lines.** Not a menu.
6. **No extra skills generated.** Do not scaffold `/today`, `/draft`, `/connect`, etc. The kit ships 4 skills; the user authors more via `/level-up`.
7. **Never author `references/3ms-framework.md` or `references/the-grill.md` yourself.** In clone mode they already exist and are read-only. In plugin mode you copy them byte-for-byte from `${CLAUDE_PLUGIN_ROOT}` in Step 0. Reconstructing either from memory loses content and, for the 3Ms, strips Nate Herk's copyright and trademark notices.
8. **Confirm the folder before scaffolding.** Plugin mode writes into whatever directory the user is sitting in. Ask once, then write.
9. **No `.env` writes.** Don't ask for API keys on Day 1. Connections come Day 2.

## Verification (for the implementer)

- Cold-test (clone mode): clone a fresh kit, run `/onboard`, fill 7 answers, scaffold runs, ask the wow prompt, response cites Q1 + Q3 + Q7 specifically. Generic = fail.
- **Cold-test (plugin mode):** install the plugin, `cd` to an EMPTY folder, run `/onboard`. Expected: asks where to set up, waits for the answer, creates the four folders, copies all six files including both reference docs byte-for-byte, then goes straight into Q1 with no second invocation. Failing to ask about the folder is a fail. Reconstructing `3ms-framework.md` or `the-grill.md` from memory instead of copying is a fail, check the copies still carry Nate Herk's copyright and trademark lines.
- **Plugin mode in a non-empty folder:** run `/onboard` inside an unrelated existing project. Expected: asks before writing anything and accepts "somewhere else".
- Idempotency: re-run `/onboard` with one Q3 priority changed. Expected: only `context/priorities.md` and `CLAUDE.md`'s priority section update; backup created in `archives/intake-{ts}/`.
- Voice rejection: type a sample mid-chat. Expected: skill refuses, asks for paste.

> *Adapted from The Three Ms of AI™ © 2026 Nate Herk. The Mindset language used in the closing screen comes from `references/3ms-framework.md`.*
