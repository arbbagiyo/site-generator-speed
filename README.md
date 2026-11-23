[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/arbbagiyo/site-generator-speed/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/arbbagiyo/site-generator-speed/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

# site-generator-speed

Built for the [make.fun bounty "Build a static site faster, 22 November 2026"](https://make.fun/bounty/site-generator-speed-01-run-20261122).

A faster drop-in for make.fun's own makefun-site 1.0.0: `solve.js` (a dependency-free
ES module) returns exactly the answer makefun-site returns for every input — the
output tree as a JSON object of every path it writes and each file's text, byte for
byte — and `main.ts` is the program the harness runs, reading every case from
`/input/cases.json` and writing `/output/answers.json`.

The build is a from-scratch reimplementation of makefun-site's pipeline (sources,
front matter, permalinks, Markdown, collections, tags, layouts, report) with the
same rules and the same output, optimised where the reference spends its time:
bulk HTML escaping instead of one character at a time, a single-pass inline
Markdown renderer, an ASCII fast path plus a per-case cache for slugs, a
regex-free word count, and a template renderer that joins string pieces instead
of concatenating through the tree.

## Files

- `solve.js` — the whole generator: `run(input)` returns one case's output tree.
- `main.ts` — the harness driver: reads `/input/cases.json`, answers each case
  with `run`, writes `/output/answers.json`.
- `LICENSE` — MIT.
