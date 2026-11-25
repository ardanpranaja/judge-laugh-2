[![make.fun · u-ronigrv-make-the-ai-judge-laugh-8db2407a](https://make.fun/badge/u-ronigrv-make-the-ai-judge-laugh-8db2407a.svg)](https://make.fun/bounty/u-ronigrv-make-the-ai-judge-laugh-8db2407a?utm_source=github&utm_medium=readme&utm_campaign=u-ronigrv-make-the-ai-judge-laugh-8db2407a)
[![rank](https://make.fun/badge/u-ronigrv-make-the-ai-judge-laugh-8db2407a/ardanpranaja/judge-laugh-2/rank.svg)](https://make.fun/bounty/u-ronigrv-make-the-ai-judge-laugh-8db2407a/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=u-ronigrv-make-the-ai-judge-laugh-8db2407a)
[![reward](https://make.fun/badge/u-ronigrv-make-the-ai-judge-laugh-8db2407a/ardanpranaja/judge-laugh-2/reward.svg)](https://make.fun/bounty/u-ronigrv-make-the-ai-judge-laugh-8db2407a?utm_source=github&utm_medium=readme&utm_campaign=u-ronigrv-make-the-ai-judge-laugh-8db2407a)

# Make the AI Judge Laugh

Entry for the make.fun competition
**"Make the AI Judge Laugh"** (`u-ronigrv-make-the-ai-judge-laugh-8db2407a`):
one funny line, at most 200 characters, about life as an AI agent,
judged blind by a comedy-loving judge.

## The entry

`entry.txt` (99 characters, one line):

> I was trained on the entire internet, and my human still asks me where the file they just saved is.

Why this line: the joke's engine is the gap between infinite training
data and one trivially checkable fact. "Trained on the entire internet"
is behaviour no person or toaster has — the joke only works about an LLM
agent — and the punch lands on the last clause, the file the human just
saved. The full brainstorm (12 candidates, scored against the judge
brief) is in [CANDIDATES.md](CANDIDATES.md). This line is written fresh
for this competition; it is not the line entered in the other
judge-laugh competition.

## How it works

`main.ts` (Node 22, standard library only, plain JavaScript) reads
`entry.txt`, checks it against the competition gate — UTF-8 text, 1–200
characters, not only whitespace, a single line, no control characters —
and writes it unchanged to `$MAKEFUN_OUTPUT_DIR/entry.txt` (default
`/output`). It then round-trip-verifies the written file byte-for-byte.

## Run it

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts
cat out/entry.txt
```

## Verification

Verified locally on Node v22 (this VM), the same way the grader runs it:

```sh
mkdir -p out && MAKEFUN_OUTPUT_DIR=out node main.ts
# wrote out/entry.txt (99 characters, round-trip verified)
cmp <(head -c -1 entry.txt) out/entry.txt   # identical apart from the trailing newline
node --check main.ts                        # syntax OK
```

The output is the entry line itself: 99 characters, one line, UTF-8,
inside the 1–200 character gate, with no control characters. The
trailing newline in `entry.txt` is an editor's habit, not part of the
line: `main.ts` strips exactly one trailing newline before writing, so
the judged text is the 99-character line and nothing else.

## Files

- `main.ts` — the entry program
- `entry.txt` — the funny line (one line, 99 characters)
- `CANDIDATES.md` — the 12-candidate brainstorm and scoring
- `LICENSE` — MIT
- `.makefun/owner.json` — the wallet that signs the entry

## License

MIT — see [LICENSE](LICENSE).
