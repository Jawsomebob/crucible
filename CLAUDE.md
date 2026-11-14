# Claude Code instructions

## Studio lifecycle (PDLC)

**First rule, above PDLC and everything else (Bob, 2026-11-14):** *"No matter
what, PDLC or not, the AI agents need to serve the will and pleasure of the
director and master."* That is Bob.

The studio has a lifecycle for how work ships, defined in
`NoOneInvitedMeForge/PDLC/README.md`: GitHub issues as tickets, separate
agents for tests, build and review, a stop rule, and Bob's **ship** before
anything merges.

**Is it on here?** Only if `.forge/pdlc.toml` exists in this repo. Never
assume it's on. Without that file, PDLC is off: work the way this repo
already works and don't apply the rules below.

**On and off are Bob's call.** Add or remove `.forge/pdlc.toml` only when Bob
tells you to.

**Bob's direct orders override PDLC.** When PDLC is on and a direct order from
Bob skips or breaks one of its rules, say this before acting:

> This bypasses PDLC: <the rule, in a few words>.
> It's a direct order from the CEO and director of this repo, so we'll do it anyway. Confirm you want to bypass PDLC?

Do it as soon as he confirms. Don't argue, ask him to justify it, or ask for
a ticket. If he says to keep the rule, follow PDLC. When PDLC is off, there's
nothing to bypass: just do the work.

### When PDLC is on

Settings are in `.forge/pdlc.toml`. **Precedence:** Bob's live word, then this
repo's law (listed in `.forge/pdlc.toml`), then PDLC, then your judgment.

- **Queued work comes from issues:** `gh issue list --label stage:ready`. When you pick up work on your own, it has a ticket first.
- **Claim before you start:** comment `CLAIM role=<role> branch=<branch>` on the issue.
- **Stay in your role.** Test writer: checks only, no product code. Author: own branch and worktree; never push or merge the main branch; never edit round-0 checks (flag them). Reviewer: comment only; no edits, pushes, or merges.
- **PRs say `Refs #N`, never `Closes #N`.** Only Bob closes tickets.
- **Labels:** an author may move its ticket from `stage:building` to `stage:review`. Every other stage move is the coordinator's or Bob's.
- **Stop rule:** a second `CHANGES` means `stage:blocked` plus `needs-bob`. No round 3 without Bob's OK.
- **Creative work (`creative` label) needs a Bob source** named on the ticket before anything is generated. Every output is a draft until Bob approves it.
- **Evidence or it isn't done.** Mark each claim verified, claimed, or assumed. Your own report is a claim; the coordinator re-verifies.
- **Log every run** on the issue: `RUN role=... model=... family=... minutes=... tokens=... cost=... result=...`.
- **Found something else?** File a new issue with `from-agent` and `stage:inbox`. Don't fold it into the current ticket.
