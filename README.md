# writeups

Technical writeups of work that is already public — the bug, the wrong turn, and the
rule I took away from it. Every claim in these posts points at a public issue, pull
request or sanitizer trace, and the claims are re-checked weekly by
[sushant-me/reputation](https://github.com/sushant-me/reputation), which goes red when
one stops holding.

## Posts

| date | post | about |
|---|---|---|
| 2026-09-19 | [The crash that wasn't: how AddressSanitizer showed my fix was for the wrong bug](2026-09-19-the-crash-that-wasnt.md) | A passing memory-safety test that segfaulted in CI; an out-of-bounds read whose fatality depends on allocator layout; closing my own pull request after the trace proved the patch was for a different bug. |

## Why these are written this way

Most engineering writeups show the solution. These show the measurement that changed
my mind, because that is the part I actually needed to read first — and because a
writeup that only contains successes cannot be checked against anything.

If a post here becomes wrong — the pull request gets closed unmerged, the bug turns
out to be a duplicate — the reputation script fails and the post gets corrected rather
than quietly left standing.
