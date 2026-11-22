# site-generator-speed-20261122

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/Kkajasd/site-generator-speed-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/Kkajasd/site-generator-speed-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

Write a faster drop-in for make.fun's own makefun-site 1.0.0 that answers exactly as it does on every case; places go by CPU time, least first, and beating makefun-site, the house baseline, at 95% confidence only qualifies an entry for a place.

A dependency-free ES module (`solve.js`) that reproduces makefun-site 1.0.0's static-site build exactly — its front-matter grammar, template dialect, Markdown subset, slug rule, link resolution and build report, byte for byte — with tight loops instead of the reference's token objects and per-character escaping: front matter is scanned by index instead of splitting the whole body, Markdown renders straight from its lines, inline markup jumps between specials with a regex scan, slugs are memoised per build, words are counted without allocating, templates render into one shared output array, and `escapeHtml` returns clean strings untouched. The driver (`main.ts`) reads every case from `/input/cases.json`, answers each with `run()`, and writes `/output/answers.json`.

Local practice set (3 cases, fresh-process CPU time for `run()` only): ~415 ms vs the house baseline's ~880–940 ms, about 2.1× faster. The official scorer passes 3/3 cases, and two runs of the full driver are byte-identical.

## Run it

```sh
node main.ts
```

(Outside a container, point `MAKEFUN_INPUT_DIR` at a directory holding `cases.json` and `MAKEFUN_OUTPUT_DIR` at the output directory.)

---

<sub>Entered on [make.fun](https://make.fun/?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>
