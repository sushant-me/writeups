# writeups

Technical writeups of work that is already public — the bug, the wrong turn, and the
rule I took away from it. Every claim in these posts points at a public issue, pull
request or sanitizer trace, and the claims are re-checked weekly by
[sushant-me/reputation](https://github.com/sushant-me/reputation), which goes red when
one stops holding.

## Posts

| date | post | about |
|---|---|---|
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
