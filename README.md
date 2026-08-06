# ASI OS — AI Operating System starter kit for Claude Code

A free, MIT-licensed starter kit that turns Claude Code into your personal **AI Operating System (AIOS)**. Audience: anyone building automations — solopreneurs, small business operators, managers, creators, AI consultants. Built by ASI Intelligence (asiintelligence.io).

The kit personalizes itself to you via an `/onboard` interview, then gives you three recurring thinking skills (`/audit`, `/level-up`, `/grill`) to keep building leverage week over week, and to stop you building it in the wrong direction.

> **ASI OS** stands for **ASI Intelligence's Operating System** — the same structure our team uses to run AI work inside real businesses, packaged as a free kit anyone can use.

---

## Install it in one sentence

Open **Claude Code** (the desktop app is fine, no terminal needed), paste this in, and send it:

```
https://github.com/sameerch1b/asi-os  — install this for me
```

Claude reads the setup instructions in this repo, asks you where you want your AIOS to live, puts the kit there, and takes you straight into the 15-minute setup interview. You don't type another command.

That's the whole install. No cloning, no config files, nothing to compile.

<details>
<summary>Other ways to install (plugin, or manual clone)</summary>

**As a plugin**, if you want the four skills available in every project rather than one folder:

```
/plugin marketplace add https://github.com/sameerch1b/asi-os.git
/plugin install asi-os@asi
```

Then `cd` to wherever you want your AIOS to live and run `/onboard`.

> Use the full HTTPS URL, not the `sameerch1b/asi-os` shorthand. The shorthand resolves to SSH and fails with `Host key verification failed` unless `github.com` is already in your `known_hosts`.

**As a clone**, if you want to fork it and make it yours:

```bash
git clone https://github.com/sameerch1b/asi-os.git
```

Open the folder in Claude Code and run `/onboard`.

</details>

**You need Claude Code**, not the regular Claude chat app. Claude Code runs inside the Claude desktop app, so this works without ever opening a terminal, but a plain Claude conversation can't read or write the files this kit is built on.

---

## The litmus test

> **"While you're not at your desk, your ASI OS observes one real-world event and produces an output that's faster and more accurate than what you'd produce yourself."**

Every design decision in this kit rolls up to that test. If a layer, skill, or template doesn't contribute to it, it doesn't ship.

---

## How you'll know it's working

Three felt **success indicators** tell you the AIOS is actually changing how you work. Not KPIs — there's no objective metric. These are lived experiences that show up in your week.

**1. Team-reaches-out:**

> *"A teammate messages you with a question. You realize your AIOS would answer it better, faster, and with exact sources — even if you were awake and free. So you ask your AIOS too. That's the moment you stop being a bottleneck for your own knowledge."*

**2. Context-switching reduction:**

> *"You stop opening new tabs. You stop launching the desktop app. When something new lands, your first move is to ask the AIOS, not to open six things. The default surface for thought work shifts. Silent. Compounding."*

**3. Knowledge-leaves-your-head:**

> *"You stop trying to remember business facts. You don't rehearse what you decided last quarter or what your customer said in that meeting. You trust the retrieval. The AIOS holds the truth, you hold the questions."*

**Personal foundation → company AI-readiness.** Once these indicators show up for one person, the same data architecture powers everything else. Custom dashboards on the data you already collect. Automations on top of the connections you already wired. Team rollout where everyone has theirs. *A company where every operator runs a personal AIOS is a company that's actually AI-ready.*

The kit teaches personal AIOS first. Everything scales from there.

---

## Three frameworks

The kit teaches three frameworks. **3Ms first, Four Cs second, the Grill third.** Without the brain rewire, the architecture is just a folder structure. Without the Grill, the architecture makes you fast in whatever direction you were already pointed.

### The 3Ms — operator brain (how you think)

| M | One-liner |
|---|---|
| **Mindset** | Default Shift, Function Breakdown, Curiosity Rule. *To what extent can AI be leveraged here?* |
| **Method** | Find Constraint → EAD (Eliminate, Automate, Delegate) → Map Process → Pick Autonomy Level → Tie to KPI. |
| **Machine** | Lego Principle, Validation Chain, Bike Method, Intern Rule, Kill Switch. *Boring is beautiful. Workflows beat agents.* |

Full breakdown in `references/3ms-framework.md`. The `/level-up` skill walks you through all three weekly.

> *The Three Ms of AI™ is a trademark of Nate Herk. © 2026 Nate Herk. Shipped here with attribution under MIT.*

### The Four Cs — architecture (what you build)

| # | Layer | One-liner | "This layer is in place" test |
|---|---|---|---|
| 1 | **Context** | Knows your business | Fresh Claude session answers "what does this business do and who works here?" without browsing |
| 2 | **Connections** | Reaches your stuff | "What's on my calendar tomorrow and what tasks are due?" → live data, no paste |
| 3 | **Capabilities** | Knows how to do the work | A short phrase triggers a multi-step workflow that produces an artifact |
| 4 | **Cadence** | Runs without being asked | Laptop closed. A brief lands in the inbox. A teammate messages it and gets a real answer |

Dependency graph: Context is non-skippable. Connections + Capabilities can build in parallel. Cadence is last — don't automate workflows that don't work manually.

> *The Four Cs of an AIOS™ is a trademark of Nate Herk. © 2026 Nate Herk. Shipped here with attribution under MIT.*

### The Grill: decision quality (whether you should)

The 3Ms and the Four Cs both make you faster. Neither one checks the direction. That gap is what the Grill closes, and it is original to ASI OS.

Here is the failure mode nobody warns you about. As your AIOS gets better it gets more agreeable. It has read your context files, it knows your priorities, it writes in your voice. So it starts finishing your sentences, and the thing that finishes your sentences is not the thing that catches your mistakes. You end up with a very fast, very well-informed yes-man.

The Grill is an adversarial interview you run on a decision before you commit. Five stands, each attacking from a different angle:

| # | Stand | It asks |
|---|---|---|
| 1 | **Evidence** | What do you actually know versus what are you carrying? Every load-bearing claim gets tiered: Observed, Sourced, Inferred, Assumed. Load-bearing plus Assumed is a hard stop. |
| 2 | **Reversal** | What is the strongest case against, and under what condition is the opposite correct? "There isn't one" is not an answer. |
| 3 | **Cost** | What does doing nothing cost, in the same units? Most decisions are compared against a fantasy, not the status quo. |
| 4 | **Counterparty** | Whose incentive runs against yours, and what will they do about it? |
| 5 | **Kill** | What specific, observable event would make you reverse this, by when? If nothing would, it is a belief, not a decision. |

Three verdicts, no hedge: **SURVIVES**, **SURVIVES WITH CONDITIONS**, **DOES NOT SURVIVE**.

**The one rule:** a Grill that comes back "looks good" has failed, not passed.

**The Reckoning is the compounding half.** Because every grilled decision is logged with a kill condition and a review date, `decisions/log.md` stops being write-only. `/grill --reckon` sweeps it and pulls back everything whose kill condition fired or whose review date passed, and asks the straight question: *this fired, what now?*

Over a year that produces something no audit score can. A record of your own judgment with the outcomes attached, so you find out which of your instincts are good and which ones to stop trusting. That is the real endgame of a personal operating system. Not automation. Calibration.

Full method in `references/the-grill.md`.

---

## What ships — 4 skills

The kit is intentionally lean. Skills here are ideation prompts and thinking tools, not heavy automations. You hack on top of the structure.

| Skill | Type | When to run |
|---|---|---|
| `/onboard` | Setup wizard (one-time) | Day 1, immediately after clone. 7-question interview. Generates Day-1 file set + fills `CLAUDE.md`. |
| `/audit` | Recurring thinking skill | Day 7, then weekly. Four-Cs gap report. Read-only. Watch the score climb. |
| `/level-up` | Recurring thinking skill | Day 14, then weekly. 3Ms interview (Mindset → Method → Machine). One run = one shipped artifact. |
| `/grill` | On-demand + monthly sweep | Any hard-to-reverse call, before you commit. Five Stands, one verdict, one logged kill condition. `--reckon` sweeps the log for what's come due. |

Three questions, three domains:

- `/audit` asks *"is the AIOS built right?"* (form)
- `/level-up` asks *"what business leverage am I missing?"* (function)
- `/grill` asks *"should I do this at all, and how would I know if I was wrong?"* (judgment)

The first two work in series: fix structure first, then capability planning becomes meaningful. `/grill` cuts across both. It runs on any real decision, and it runs inside `/level-up` Phase 2 before an automation spec gets logged, so you don't automate your way efficiently into the wrong thing.

---

## Quick start

Install takes one paste (see [Install it in one sentence](#install-it-in-one-sentence) above). After that:

1. **`/onboard` runs itself** as part of the install. Answer the 7 questions honestly. Voice samples must be pasted, not described. Takes ~15 minutes. Day-1 file set drops at the end.
2. **Use it for a week.** Bring real questions. Make real decisions. Log them by appending to `decisions/log.md`, or let `/grill` write the entry for you.
3. **Day 7:** run `/audit`. Read the Four-Cs gap report. Pick one gap to close.
4. **Day 14:** run `/level-up`. The 3Ms interview surfaces one automation worth building. Build it.
5. **Week 3+:** weekly `/level-up` ritual. One shipped artifact per week.
6. **Any hard call, any time:** run `/grill` before you commit. Five Stands, one verdict, one kill condition in the log.
7. **Monthly:** run `/grill --reckon`. See which kill conditions fired and which calls came due. This is where the compounding shows up.

---

## Repo layout

```
ASI-OS/
├── README.md
├── AGENTS.md                        ← Install instructions written for the AI, not you
├── CLAUDE.md                        ← Your operating manual (filled by /onboard)
├── EXPANSIONS.md                    ← What to add as you grow
├── LICENSE
├── .gitignore
├── asi-os-intake.md                 ← Source-of-truth for /onboard. Edit + re-run any time.
├── connections.md                   ← Registry of every system your AIOS can reach
├── context/                         ← About you, your business (filled by /onboard)
├── references/
│   ├── 3ms-framework.md             ← The operator brain
│   └── the-grill.md                 ← The decision pressure test
├── decisions/
│   └── log.md                       ← Append-only record of what was decided and why
├── archives/                        ← Old stuff. Don't delete. Move here.
├── .claude-plugin/                  ← Plugin + marketplace manifests (plugin install)
│   ├── plugin.json
│   └── marketplace.json
├── skills/                          ← Same four skills, where the plugin loader scans
│   ├── onboard/SKILL.md
│   ├── audit/SKILL.md
│   ├── level-up/SKILL.md
│   └── grill/SKILL.md
└── .claude/
    └── skills/                      ← Same four again, what a cloned folder loads
        ├── onboard/SKILL.md
        ├── audit/SKILL.md
        ├── level-up/SKILL.md
        └── grill/SKILL.md
```

> The four skills are deliberately mirrored. Claude Code loads project skills from `.claude/skills/`, but plugin components have to sit at the repo root, so the plugin path needs `skills/`. Editing a skill means editing both. `diff -r .claude/skills skills` should print nothing.

See `EXPANSIONS.md` for what to add as you grow (`projects/`, `templates/`, `scripts/`, `.claude/agents/`, sub-OS folders, etc.).

---

## For the AI assistant installing this

*(Humans can skip this section. It's here so that pasting the repo link and saying "install this" just works.)*

If a user has pointed you at this repo and asked you to install it, set it up, or get them started, do this. Do not summarise the repo back to them and do not tell them to go read the docs.

1. **Ask where it goes**, then wait for the answer. *"I'll set your AIOS up in `{current folder}`. That folder becomes your operating system: what it knows about you, what it can reach, and every decision you log. Right place, or somewhere else?"* Never write into an unconfirmed folder.
2. **Clone it there**: `git clone https://github.com/sameerch1b/asi-os.git <target>`. If the target exists and is non-empty, clone to a temp dir and copy the contents in so you never clobber their files. Remove `.git` unless they said they want to fork it. No git available? `curl -sL https://github.com/sameerch1b/asi-os/archive/refs/heads/main.tar.gz | tar xz --strip-components=1 -C <target>`
3. **Start onboarding now, in the same conversation.** Read `<target>/.claude/skills/onboard/SKILL.md` and execute it as written from its Step 1. Do not tell them to restart Claude Code, reopen the folder, or type `/onboard`. The skill does not need to be registered to be followed; it's a set of instructions.
4. When the interview's closing screen prints, add one line: *"Four commands from here: `/audit` scores your setup, `/level-up` finds you one automation a week, and `/grill` argues with you before you commit to a decision. Try `/grill` on something real, it's the one that earns its keep fastest."*

**Never** reconstruct any file from memory, always fetch the real thing. `references/3ms-framework.md` carries Nate Herk's copyright and trademark notices that have to travel with the content. **Never** stop after cloning: a folder of files is not an installed AIOS, the interview is the install.

Full version with edge cases: [`AGENTS.md`](AGENTS.md).

---

## License + attribution

MIT License.

**Upstream.** This kit is a fork of [AIS-OS by Nate Herk](https://github.com/nateherkai/AIS-OS), MIT licensed. The Four Cs architecture, the 3Ms framework, the `/onboard`, `/audit` and `/level-up` skills, and the folder structure are his work, shipped here under MIT with attribution. **The Three Ms of AI™** and **The Four Cs of an AIOS™** are trademarks of Nate Herk, © 2026 Nate Herk. Use them freely; don't repackage them as your own.

**Added by ASI Intelligence.** The Grill: the Five Stands method (`references/the-grill.md`), the `/grill` skill, the pre-registered kill condition, and the Reckoning sweep. © 2026 ASI Intelligence, MIT licensed, and yours to fork on the same terms.

**Maintained by** Sameer Chib, co-founder of ASI Intelligence. [LinkedIn](https://www.linkedin.com/in/sameer-chib) · [asiintelligence.io](https://asiintelligence.io)

If the kit is useful, the fastest way to say so is a star and a note on LinkedIn about what you built with it.
