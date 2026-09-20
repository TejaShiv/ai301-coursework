# Unit 1 Selection

## Chosen issue

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/72

verify_password raises UnknownHashError on a malformed hash instead of failing closed.

## Skill verdict

accept. All six required checks passed and all three preferred checks passed. The skill ranked it first of three accepted candidates, ahead of #71 and #73, with the fit profile breaking the tie because #72 is a change to product code in core/security.py while #71 edits a test fixture and #73 is docs-only.

Per-check output for the chosen issue:

maintainer-alive, pass. All five latest main commits by human Aburke225, newest 2026-09-16, and maintainer replies are present on sampled issues #52 and #43.
repo-in-use, pass. Archived no, zero releases published so the push date governs, pushed 2026-09-16.
scope-bounded, pass. One symptom across two named files, stated as verification against a malformed hash should fail closed and return False rather than raise. No umbrella, no design debate, no undecided deliverable.
unclaimed, pass. Assignees empty, repo has zero PRs, zero comments on the thread.
not-a-contributor-graveyard, pass. Zero comments, so zero distinct claiming accounts.
ai-policy-permits, pass. CONTRIBUTING.md has no AI clause and no AI policy file exists, so silence passes.
maintainer-responsive, preferred, pass. Issue #52 opened 2026-09-10 and drew a maintainer response on 2026-09-16.
maintainer-endorsed, preferred, pass. Labeled good first issue and opened by a COLLABORATOR.
no-stale-attempts, preferred, pass. Opened 2026-09-10, no closed unmerged PRs.

## Run history

First full run, 14 of 20, category floor met but clear-accept only 3 of 8. Five of the six disagreements were false rejects and all five were driven by one check, maintainer-alive, which required at least two of five sampled issues to have drawn a maintainer response within 30 days.

I read the repo facts for all five. On conda/conda the repo had commits from the day before capture but 662 open issues and almost no thread replies, with the one measured response at 32.9 days, just past my line. On Itqan and lq-ai the sampled issues had been opened on or one day before the capture date, so they had no elapsed time in which to receive a reply, and one repo had a sample of exactly one. My check was punishing large backlogs and thin samples rather than measuring whether maintainers exist.

Second change in the same revision addressed the one false accept, issue-20, a feature request opened by cursor[bot] with the logo asset listed as TBD.

Partial run on the six disagreements, 5 of 6. Four false rejects flipped and the false accept flipped. issue-01 traded one failure for another and now failed scope-bounded.

I read issue-01 in full. It is a single conda documentation change written by a CONTRIBUTOR, using subheadings to describe the several pages one edit touches. My umbrella disqualifier was reading subheadings as a list of separable work items, and my TBD clause risked matching template boilerplate. I narrowed both.

Partial run on issue-01 and issue-20, 2 of 2. I re-graded issue-20 alongside it to confirm that loosening the umbrella clause had not let the bot-authored request back in.

Second full run, 18 of 20, passing the bar with the category floor met. The two disagreements were new. issue-15 and issue-19 had both agreed in the first full run and flipped here without my having changed anything aimed at them, which told me they sit in the arguable band the assignment describes.

I read both. issue-19 is one high-priority bug filed by a COLLABORATOR, a frozen UI, whose numbered lists are candidate causes and optional optimizations rather than separate deliverables. issue-15 has been open since 2021 with 97 comments in which at least eight distinct accounts claimed the work through a claim bot and were auto-unassigned for inactivity, with no merged fix. My unclaimed check passed it because every claim was older than 60 days and the assignee field was empty, and the only check that saw the pattern, no-stale-attempts, was preferred and so could not reject.

I carved numbered diagnosis and suggestion lists out of the umbrella disqualifier, and added a sixth required check, not-a-contributor-graveyard, failing any issue where three or more distinct accounts have claimed the work over its life without producing a merged fix.

Partial run on both targets plus all eight clear-accepts, 9 of 9. I included the clear-accepts deliberately, because adding a required check is the change most likely to create new false rejects and I wanted that confirmed before overwriting a passing run.

Final full run, 20 of 20, every category matched. That run is the one in eval-run.txt.

## Issue analysis

issue-15, the Zulip outgoing webhook issue at zulip/zulip#19589. My rubric graded it accept in the second full run. The gold label is reject.

My rubric read the surface facts and found nothing wrong. The assignee field was empty, no PR was linked, the issue carried both help wanted and good first issue labels, the repo was active, and the requested change itself is small and well specified, separating a command field from a text field in an outgoing webhook payload. Every check I had was satisfied.

What my rubric could not see was the thread. The issue has been open since August 2021 with 97 comments, and reading them shows at least eight distinct people claiming the work through zulipbot between 2021 and 2024, each one auto-unassigned after 14 days of inactivity, one of them reporting a PR that was never merged. The issue has attracted volunteers continuously for five years and defeated every one of them.

My unclaimed check looked only at whether a claim was recent, within 60 days, and every claim here is years old, so the check passed the issue. The evidence that mattered was not the recency of any single claim but the count of distinct claimants over the issue's life, which is a different measurement of a different thing. A first-issue label is a maintainer's estimate of difficulty made once, years ago; eight abandoned attempts are eight independent measurements of the same difficulty, and they disagree with the label.

That is what not-a-contributor-graveyard now measures.

## Check rationale

The check I most changed is scope-bounded, and its first disqualifier now reads:

"One, it is a tracking or umbrella issue, meaning it collects work that is meant to be split into separate issues or pull requests, shown by links to child issues, a checklist of independently shippable tasks, or wording asking for the work to be broken up. An issue that describes one symptom or one coherent change passes even when the body uses numbered lists or subheadings for causes, proposed approaches, optional follow-up suggestions, or the several files one change touches."

The whole check is written as a list of disqualifiers rather than a list of things an issue must show, and that shape is deliberate. My verdict rule treats unclear as fail on required checks, so a check demanding positive evidence of good scope would grade unclear on every terse issue and reject it. The evidence guide warns against exactly this, saying short is not the same as unscoped and that a terse body or a missing reproduction can still be a bounded first issue. By listing only what disqualifies, absence of evidence resolves to pass.

The second sentence exists because of a specific failure. The clause originally read only that the issue lists sub-items meant to be split apart, and on issue-01 the grader saw four Update subheadings in a single documentation change and failed it. The distinction that matters is not whether a body contains a list but whether the items in it are separately shippable. Naming the innocent cases outright, causes, proposed approaches, optional suggestions, and the several files one change touches, moved both issue-01 and issue-19 to the correct verdict without letting the genuine umbrella issues through.

## Trade-offs

The largest trade-off is between false rejects and false accepts, and my first rubric sat badly on one side of it. Every required check I wrote was a reason to reject, and with unclear counting as fail, thin evidence and strict evidence produced the same outcome. At 14 of 20, five of six errors were false rejects. The fix was not to weaken the checks but to make each pass condition state what an absent or thin signal means, so that silence resolves rather than sinking the issue.

The second trade-off is between signals that are cheap to read and signals that are correct. Commit dates are one line in the repo facts and mean roughly what they appear to mean. Maintainer response latency looks equally quantitative and is not, because it is confounded by backlog size, by sample size, and by how recently the sampled issues were opened. Demoting it to preferred cost nothing on the eval set and fixed four issues, but it means my rubric no longer rejects a repo purely for being unresponsive unless the 60-day guard fires, and a genuinely slow repo could get through.

The third is that thread reading is expensive and my rubric now depends on it. not-a-contributor-graveyard requires counting distinct claimants across 97 comments, of which only the first 40 appear in the bundle. On a truncated thread the count is a floor, not a total, which biases the check toward accepting. It caught issue-15 because eight claims appear well inside the first 40 comments, and it would miss an issue whose abandonment history sits past the truncation point.

Finally, the rubric has a wording ambiguity I did not resolve. maintainer-responsive requires a sampled issue open at least 7 days to have drawn a response within 30 days, and it is not clear from that sentence whether the 7 days qualifies the issue's age or the reply time. On the live Path Review repo the grader read it one way and passed the check on a 6-day reply to a 9-day-old issue; an earlier partial read it the other way and failed it. Since the check is preferred, no verdict moved either way, which is the only reason the ambiguity was affordable.
