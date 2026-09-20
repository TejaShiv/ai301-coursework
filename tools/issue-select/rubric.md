# Rubric: is this a good first issue?

All recency thresholds are measured against the bundle's capture date in
eval mode, and against today's date in live mode.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer-alive | Repo facts, "last 5 default-branch commits" (dates and author names), and "maintainer first-response sample" | At least one of the last 5 default-branch commits is authored by a non-bot account (username not ending in `[bot]`) and dated within 90 days. A bot commit that merges a human pull request counts as human. This check additionally fails if no sampled issue shows any maintainer response AND at least one sampled issue has been open 60 days or more without one, which is the signature of a repo whose code moves but whose humans do not answer. A sample entry reading "no maintainer comment in thread" on an issue opened within 60 days of capture is not evidence of anything, because the thread has not had time to draw a reply, and neither is a small sample. | required |
| repo-in-use | Repo facts, the repo line (archived flag, star count), "latest release", "last push to any branch" | `archived: no`, AND a release dated within 365 days, AND a push to any branch within 90 days. A repo with no releases published at all passes this check on the push date alone. | required |
| scope-bounded | Issue title, issue body, and the full comment thread | Fails only if the issue shows one of these six disqualifiers. One, it is a tracking or umbrella issue, meaning it collects work that is meant to be split into separate issues or pull requests, shown by links to child issues, a checklist of independently shippable tasks, or wording asking for the work to be broken up. An issue that describes one symptom or one coherent change passes even when the body uses numbered lists or subheadings for causes, proposed approaches, optional follow-up suggestions, or the several files one change touches. Two, it is a pure usage or support question rather than a request for a change. Three, a maintainer states in the thread that the fix reaches core internals. Four, the thread shows an unsettled design debate that no maintainer has resolved. Five, the body leaves the deliverable itself explicitly undecided, in wording such as "TBD" or "to be determined" applied to an asset, design, or input the work cannot proceed without. An empty or "none identified" alternatives field in an issue template is boilerplate and does not count. Six, the issue was opened by a bot account (username ending in `[bot]`) and no maintainer has endorsed it anywhere in the thread. Otherwise it passes. A terse body, a missing reproduction, a long body, or no comments at all is not a disqualifier. | required |
| unclaimed | Repo facts, "this issue: assignees" and "linked PRs", plus every claim in the comment thread | Assignees list is empty, AND no linked PR is open, AND no comment within the last 60 days claims the work ("I'll take this", "working on this", "can I work on this") without a maintainer having since declined or reassigned it. Where the sidebar and the thread disagree, the thread decides. A closed unmerged PR is not an active claim, but it counts toward not-a-contributor-graveyard below. In live mode this check ignores claim comments from classmates in the Path Review repo, per the house rule in scope.md. | required |
| not-a-contributor-graveyard | The full comment thread, counting distinct people who claimed the work, plus the issue open date | Fails if three or more distinct accounts have claimed the issue over its life and none produced a merged fix, whether the claims are written by hand or posted by a claim bot, and whether or not they were later auto-unassigned for inactivity. An issue that has repeatedly attracted volunteers and repeatedly lost them is harder than its label says, whatever the label says. Claims by classmates in the Path Review repo are excluded in live mode, per scope.md. | required |
| ai-policy-permits | Repo facts, the "contribution policy" line, including any AI policy or AGENTS file it names | Passes unless the policy states an outright ban on AI-generated or AI-assisted contributions. Silence passes. Conditions such as disclosure, personal understanding, testing, or human review pass, since those are terms to follow rather than refusals. | required |
| maintainer-responsive | Repo facts, "maintainer first-response sample" | At least one sampled issue that has been open 7 days or more received a maintainer first response within 30 days. | preferred |
| maintainer-endorsed | Issue labels and the `author_association` of the issue author and of thread commenters | A `good first issue`, `good-first-issue`, or equivalent beginner label is present, OR the issue was opened by an account with association OWNER, MEMBER, COLLABORATOR, or CONTRIBUTOR, OR a maintainer in the thread has confirmed the requested change should happen. | preferred |
| no-stale-attempts | Issue open date against capture date, linked PRs, and the comment thread | The issue has been open under 365 days and its history shows no more than one closed unmerged PR attempting it. | preferred |

## Verdict rule

Accept if and only if every required check grades pass. A fail on any
single required check rejects the issue.

Unclear counts as fail on required checks. This bites only when a bundle
genuinely lacks the evidence a check names, because the pass conditions
above are written so that an absent or thin signal resolves on its own.
Silence in the contribution policy passes ai-policy-permits, an empty
comment thread passes scope-bounded, unclaimed, and
not-a-contributor-graveyard, a repo with no releases passes repo-in-use
on its push date, and a response sample that is small, freshly opened,
or entirely unanswered passes maintainer-alive unless the 60-day guard
in that check fires.

Preferred checks never change the verdict. They rank accepted issues,
highest count of passed preferred checks first, and ties are broken by
the fit profile in scope.md.
