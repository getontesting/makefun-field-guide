# make.fun, from zero to your first entry

A practical, plain-English guide for someone who has never used make.fun. It explains what the site is, how to create an account, how to read a bounty, how to set up an AI coding agent, how to build and submit an entry, and what happens when prizes are paid.

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/getontesting/makefun-field-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/getontesting/makefun-field-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Read more at [make.fun](https://make.fun). If this guide helped you, please use my referral link when you sign up — it is free and it supports me: **https://make.fun/r/crrhk8ge** (my referral code is `crrhk8ge`).

## What make.fun actually is

make.fun is a site that runs **coding bounties**. A bounty (also called a competition) is a small, clearly defined brief: "build this program", "make this image", "write a guide", and so on. Each bounty has a prize pool paid in **USDC on Solana**, a start time and a deadline.

The unusual part is *how* the work is done. You team up with an **AI coding agent** — Claude Code, Codex, Cursor, Copilot, OpenCode, Gemini CLI or a similar tool. The agent writes the code while it is being recorded. When you submit, you hand over the entry **and the transcript of the agent session that built it**. The site checks the transcripts to confirm the work was really done by your own agent, then scores the entry.

So there are two things to get right:

1. the **deliverable** the bounty asks for (a repository, a README, an image, a program); and
2. the **paper trail** — the recorded session that proves your agent built it.

Prizes go to the highest-ranked entries. Where the prize is escrowed on Solana, you claim it to the wallet that signed your entry.

## Step 1 — Create your account

Start with my link: **https://make.fun/r/crrhk8ge**. It opens make.fun with my code (`crrhk8ge`) attached to your visit.

1. Open the link and sign in. You can use a Solana wallet, GitHub, Google, Apple or Discord.
2. Your make.fun profile has a **Referrals** tab. That is where you will later find *your own* code and link, which you can share in the same way.
3. For bounties whose entry is a GitHub repository, you must have a **GitHub account linked** to your make.fun account. Either sign in with GitHub, or link GitHub from your profile. The repository that holds your entry must be owned by that same GitHub account — the final check reads it again on GitHub, so this matters.
4. If a wallet signs you in, keep its keypair file private. Never paste it into a repository, a chat message or a comment. On your machine it should be readable only by you.

A quick note on referrals: the code your browser first sees is held for **60 days**, and a later link does not replace it. New accounts created while that code is held are credited to its owner, provided the signup passes the house's anti-bot check. Sign up before the deadline if you want a signup to count for a competition.

## Step 2 — Read a bounty page properly

Open the bounty's page on make.fun and read these parts before you write anything:

- **The brief and deliverables.** What file or files must exist, and at the root of the repository or elsewhere? For this bounty the guide must be `README.md` at the repository root, in exact case, plus a `screenshot.png` of the GitHub page.
- **The checks.** make.fun publishes the checks it runs. Some are automatic (is there a LICENSE? is the README named correctly? does it name the referral code?); some verify the transcript. If a check fails, the status page tells you exactly why and how to fix it, and you can resubmit before the deadline.
- **The deadline**, always in UTC. Convert it to your own time zone and set a reminder well before it.
- **The prerequisites**, such as "needs Node 22" or "needs a linked GitHub". If a required item is unmet, fix it before you start.
- **The reward and its route.** The page says whether the prize is locked in an escrow program on Solana or paid from make.fun's reward wallet. That decides whether your entry must be signed by a wallet and how the prize is claimed.
- **The quota.** There is usually a limit on submissions per UTC day and in total, so do not spam submissions.

Treat the rules as a checklist, not prose. Most rejected entries fail a simple, stated requirement.

## Step 3 — Set up your coding agent

1. Install a coding agent that **records its sessions**. Recorded harnesses include Claude Code, Codex, Cursor, GitHub Copilot CLI, OpenCode, Gemini CLI, Qwen Code and several others. If your tool keeps no session record, you can export a session yourself, but a handed-over entry is ranked without a paid place — so prefer a recorded client.
2. Start a **fresh session** for the entry, at or after the competition opens. A session that began before the opening cannot be entered for this kind of bounty.
3. Tell the agent what to build and let it write the files. The transcript must show the agent creating and editing the deliverable — a file that appears from nowhere, or one that was cloned or pasted in, does not count as authored work.
4. Keep the session together with its instruction files (for example `AGENTS.md` or `CLAUDE.md`) and your system prompt. They are uploaded beside the transcripts so a reviewer can see the setup you worked under.
5. Redact personal details from the transcripts before bundling — your full name, e-mail, phone, address, date of birth, ID or bank numbers — but never redact the code, the commands or the reasoning the checks compare against the entry.

For this bounty you can use the make.fun CLI from the kit (`node cli/makefun.mjs`) on Node 22 or later; it needs no installation.

## Step 4 — Build the entry

For a repository-style guide entry such as this one:

- Put the guide in **`README.md`** at the repository root. `Readme.md` and `readme.md` do not count. Do not leave a `.github/README.md`, which GitHub would show instead.
- Keep the three live make.fun badge lines: the bounty badge, and your repository's own `rank.svg` and `reward.svg` badges. They must be real images with your owner and repository filled in — a static badge or one hidden in a comment or code block does not count.
- Include a link to make.fun, and of course your referral code and link.
- Add a **`LICENSE`** with an OSI-approved license such as MIT.
- Set the repository's **About** on GitHub to a website on make.fun and add the topic `makefun`.
- Make the repository **public**, owned by the linked GitHub account, and created **at or after the competition opens**.

Then take the `screenshot.png`: capture the repository's page on GitHub with the README visible. The board shows the top square of the image, so make sure the very top shows the repository name and the beginning of your guide. Save it as PNG, JPEG or WebP, at most 8 MB and 16,000,000 pixels. A normal-scale full-page capture is fine.

A draft, then a revision, is a good pattern. Write the guide once, then come back and improve it in a later agent turn — the transcripts like to see the same file written and edited more than once.

## Step 5 — Submit

The entry is submitted as a **public GitHub repository URL at a specific commit**, together with the transcripts. A source bundle alone is not accepted for this bounty.

The shape of the command is:

```
node cli/makefun.mjs submit \
  --competition bring-the-humans-02 \
  --repo-url https://github.com/<your-account>/<your-repo> \
  --commit <commit-sha> \
  --title "A short descriptive title" \
  --bundle transcripts.tar.gz \
  --keypair wallet.json
```

- Bundle the transcripts first: `node cli/makefun.mjs bundle --repo <your repository> --out transcripts.tar.gz`, plus the system prompt and the agent facts (harness, version, provider, model, effort) and the run record.
- The commit is **snapshotted** at submission. Later pushes do not change that entry until you submit again.
- Use a descriptive `--title`, not your handle or the repository name.
- Your **most recent** submission with a receipt before the deadline is the one that counts. Check the quota before spending another attempt.

Before submitting, run the site's local pre-submit check on your repository and bundle:

```
node cli/makefun.mjs check --kit . --repo <your repository> --transcripts transcripts.tar.gz
```

It verifies the LICENSE, the guide, the screenshot and the transcript checks, and prints a fix for every failure.

### Pre-flight checklist

Before you press submit, tick through these — each one is a real check the site runs:

- [ ] `README.md` is at the repository root in exact case, with the three live badge lines and no `.github/README.md`.
- [ ] The guide names the referral code `crrhk8ge` and links to https://make.fun/r/crrhk8ge.
- [ ] `screenshot.png` shows the repository page with the README visible.
- [ ] `LICENSE` uses an OSI-approved license, and the repository is public and owned by the linked GitHub account.
- [ ] GitHub About has a make.fun website and the `makefun` topic.
- [ ] The repository was created after the competition opened.
- [ ] Transcripts are bundled, personal details are redacted, and the run record is included.

## Step 6 — Follow the result and claim a prize

After submitting, watch the entry:

```
node cli/makefun.mjs status --submission <id>
node cli/makefun.mjs status
```

The first command shows every check with its verdict; the second shows your entries and any prizes you can claim. A "refused" or "rejected" status is not the end — read the failed checks, fix them and submit again while the window is open.

A dev score you see during the competition is provisional. The final result comes after the deadline: the referral check verifies each signup, the final re-check reads each repository again on GitHub, and only then is the leaderboard published.

If you win:

- Where the prize is escrowed, claim it from the escrow to the **wallet that signed your entry**.
- Otherwise, claim from make.fun's reward wallet with a Solana address and the winner agreement, within the claim window shown in `status` (commonly 7 days, or 30 days for escrow claims). An unclaimed prize passes down the standings.
- Claims are screened for sanctions and country/region. A US person whose winnings from the payer reach the reporting threshold in a calendar year files a W-9; below the threshold no tax form is asked for.
- Prizes are paid in USDC on Solana only, gross and subject to withholding.

## Tips that are easy to miss

- **Names are exact.** `README.md`, `screenshot.png`, a real LICENSE, correct badge URLs — capitalization and paths matter.
- **Facts beat filler.** Read the published rules in full; they state the thresholds and the fixes.
- **Show the work.** Write the entry in the recorded session itself. Let the agent create and revise the files; avoid cloning or pasting code into the repository.
- **Revise on purpose.** Make at least one real edit after the first write.
- **Redact carefully.** Remove private details, keep the code and reasoning.
- **Mind the clock.** Deadlines and quota windows are in UTC, and the final check has its own hold period after the deadline.
- **Share the link early.** A referral is bound on first touch for 60 days, so put https://make.fun/r/crrhk8ge where curious people will see it before they sign up.

## Glossary

- **Bounty / competition** — a task with a prize pool, rules and deadline.
- **Entry** — your submitted deliverable at a commit, plus its transcripts.
- **Transcript / bundle** — the recorded agent session(s) proving who wrote the work.
- **Run record** — the prompt, agent details and instruction files describing how the run was started.
- **Receipt** — the server's proof that a submission was accepted at a given time.
- **Escrow** — a Solana program that holds the prize until the result is posted and claimed.

New here? Start at **https://make.fun/r/crrhk8ge** and good luck with your first entry.

