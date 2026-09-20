# writeups

Technical writeups of work that is already public — the bug, the wrong turn, and the
rule I took away from it. Every claim in these posts points at a public issue, pull request, sanitizer
trace or security advisory, and the claims are re-checked weekly by
[sushant-me/reputation](https://github.com/sushant-me/reputation), which goes red when
one stops holding.

## Posts

| date | post | about |
|---|---|---|
| 2026-09-21 | [The check that could not see what it was checking](2026-09-21-the-check-that-could-not-see-what-it-was-checking.md) | Seven instances of one defect: a check reads a reduced form of its input and reports success when the reduction removed what it was looking for. A PDF guard that compared only numbers and missed five stale city names; a reproducibility check that re-runs the analysis over **already-parsed decisions** and so could not see a 14.5% change in the parser; a masker that deleted the word a rule matched on; a form filler that logged answers it never gave. Includes the measured effect on a published metric — every structured condition unchanged to the digit, the headline comparison intact — and why the committed results were left alone. |
| 2026-09-21 | [Four checks that ran on data something else had already rewritten](2026-09-21-four-checks-that-ran-on-rewritten-data.md) | Four security advisories from auditing my own tools, and the shape they share: the check ran on data an earlier line had already transformed. A regex without `DOTALL` turned `send_\nemail` into an allowed call in the policy gate; an unbounded read let a hostile MCP server kill the scanner inspecting it; a masker blanked the one-line constant a rule matched on; a Unicode range list covered 16 of 256 variation selectors and the gap also survived the helper meant to show what text really contains. Plus the sixth instance, in the script that verifies every claim in these posts: a PDF that could not be read passed every PDF assertion, because an empty string has no numbers that are not a subset. And the finding that mattered more — the fixes were not reaching users at all, because the documented `@v1` action tag was four releases stale. |
| 2026-09-21 | [A number nothing recomputes](2026-09-21-a-number-nothing-recomputes.md) | Ten wrong facts in things I had already published — a CV, a profile, a hire page, a paper's README, a released product — each of them true when written. Why the claim verifier I already had could not see any of them, and the ~370 lines that now make each one repeatable: forbidden strings carrying their reasons, required corrections so a fix-by-deletion fails, counts derived from the source file, and coverage asserted so a run that read nothing cannot pass. Includes the escape hatch I refused to add, and the three times this post failed its own check. |
| 2026-09-21 | [A benchmark found a bug in my own detector](2026-09-21-a-benchmark-found-a-bug-in-my-own-detector.md) | I built a labelled corpus to stop making unmeasured claims, and it immediately found a false positive in my own scanner — precision 0.750 → 1.000, with the failing case named in CI rather than deleted. The benchmark was wrong twice before that, the harness assumed its author's output format, and the guard added for the fix surfaced a third defect: the release reported the wrong version. Three defects, one shape — a number nothing checked. |
| 2026-09-20 | [Structured output made my safety evaluator less safe](2026-09-20-structured-output-made-it-less-safe.md) | The counter-intuitive result behind my paper: JSON-constrained output without a reasoning field approved 46.2% of proposals the policy would have blocked, against 17.2% for free-form — and the fastest configuration was the least safe. Every number here is checked against the paper's own README and the source repository. |
| 2026-09-19 | [The crash that wasn't: how AddressSanitizer showed my fix was for the wrong bug](2026-09-19-the-crash-that-wasnt.md) | A passing memory-safety test that segfaulted in CI; an out-of-bounds read whose fatality depends on allocator layout; closing my own pull request after the trace proved the patch was for a different bug. |

## Why these are written this way

Most engineering writeups show the solution. These show the measurement that changed
my mind, because that is the part I actually needed to read first — and because a
writeup that only contains successes cannot be checked against anything.

If a post here becomes wrong — the pull request gets closed unmerged, the bug turns
out to be a duplicate — the reputation script fails and the post gets corrected rather
than quietly left standing.
