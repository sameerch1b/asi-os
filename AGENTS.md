# For the AI assistant reading this

Someone has pointed you at this repository and asked you to install it, set it up, or get them started. This file tells you exactly what to do. Follow it top to bottom.

**Do not** summarise the repo back to them, do not print the README, and do not tell them to go and read the docs. Install it and start the interview. That is the whole job.

---

## What this is

ASI OS turns Claude Code into the user's personal AI Operating System. It is a folder structure plus four skills. It is not a program, there is nothing to compile, and it has no dependencies.

---

## Step 1: Ask where it goes

One question, then wait:

> "I'll set your AIOS up in `{current folder}`. That folder becomes your operating system: what it knows about you, what it can reach, and every decision you log. Is that the right place, or somewhere else?"

Rules:
- Never write into a folder they have not confirmed.
- If the current folder already holds an unrelated project, say so and suggest a fresh one.
- If they name a folder that does not exist, create it.

## Step 2: Put the kit in that folder

```bash
git clone https://github.com/sameerch1b/asi-os.git <target-folder>
```

If the target folder already exists and is not empty, clone to a temporary directory and copy the contents in, so you never clobber their files:

```bash
git clone https://github.com/sameerch1b/asi-os.git /tmp/asi-os-src
cp -R /tmp/asi-os-src/. <target-folder>/
rm -rf <target-folder>/.git /tmp/asi-os-src
```

Drop the `.git` directory unless they said they want to fork it. Most people want their own kit, not a checkout tracking someone else's repo.

**No git available?** Download the tarball instead:

```bash
curl -sL https://github.com/sameerch1b/asi-os/archive/refs/heads/main.tar.gz | tar xz --strip-components=1 -C <target-folder>
```

Confirm the folder now contains: `CLAUDE.md`, `asi-os-intake.md`, `connections.md`, `EXPANSIONS.md`, `context/`, `references/`, `decisions/`, `archives/`, and `.claude/skills/` holding `onboard`, `audit`, `level-up` and `grill`.

## Step 3: Start onboarding immediately, in this same conversation

This is the step people get wrong. **Do not** tell them to restart Claude Code, reopen the folder, or type `/onboard`. They asked you to set it up, so set it up.

Read `<target-folder>/.claude/skills/onboard/SKILL.md` and execute it now, as written, starting from its Step 1. You do not need the skill to be registered as a slash command. It is a set of instructions and you can follow them directly.

The interview is 7 questions and takes about 15 minutes. Its Q2 has a hard rule about pasted writing samples: honour it, it is there for a reason.

## Step 4: Tell them what they have

When `/onboard` finishes it prints its own closing screen. Let it. Add nothing except this, once:

> "That's it. Four commands from here: `/audit` scores your setup, `/level-up` finds you one automation a week, and `/grill` argues with you before you commit to a decision. Try `/grill` on something real, it's the one that earns its keep fastest."

---

## If they would rather install it as a plugin

Some people want the skills available in every project rather than one folder. That path is two commands **they** type, because `/plugin` is a user command and you cannot run it for them:

```
/plugin marketplace add https://github.com/sameerch1b/asi-os.git
/plugin install asi-os@asi
```

Use the full HTTPS URL. The `sameerch1b/asi-os` shorthand resolves to SSH and fails with `Host key verification failed` on any machine that does not already have `github.com` in its `known_hosts`.

After they run those two, `/onboard` handles the folder scaffolding itself.

---

## Things that will make this go wrong

- **Do not reconstruct any file from memory.** Clone or download the real thing. `references/3ms-framework.md` carries Nate Herk's copyright and trademark notices that must travel with the content.
- **Do not scaffold into an unconfirmed folder.**
- **Do not stop after cloning.** A folder of files is not an installed AIOS. The interview is the install.
- **Do not skip Q2's paste rule** by writing sample text yourself. The voice samples must be the user's own unedited writing.
- **Do not add extra skills.** The kit ships four. Users author more through `/level-up`.

---

MIT licensed. Fork of [AIS-OS by Nate Herk](https://github.com/nateherkai/AIS-OS). The Grill is original to ASI OS. Full attribution in `LICENSE` and the README.
