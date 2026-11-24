# agent-postmortem

[![make.fun · u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3](https://make.fun/badge/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3.svg)](https://make.fun/bounty/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3?utm_source=github&utm_medium=readme&utm_campaign=u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3)
[![rank](https://make.fun/badge/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/nmlyz/agent-postmortem/rank.svg)](https://make.fun/bounty/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3)
[![reward](https://make.fun/badge/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3/nmlyz/agent-postmortem/reward.svg)](https://make.fun/bounty/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3?utm_source=github&utm_medium=readme&utm_campaign=u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3)

agent-postmortem writes a one-sentence postmortem of a coding agent's worst misunderstanding to a text file: asked to use the library the project already had, the agent invented a function in that library that does not exist, imported it, and the build failed in CI while it passed locally — because it had also written the invented function into node_modules. One sentence, 233 characters: what was asked, what the agent did instead, and what broke, with the turn in the last clause.

## Run it

```sh
python3 main.py
```

It writes the story to `/output/entry.txt` (or `$MAKEFUN_OUTPUT_DIR/entry.txt` when that variable is set). No network access needed; the same text, byte for byte, on every run.

## How it works

`main.py` is a single self-contained program using only the Python standard library:

- The story is held in one constant, `ENTRY`, so there is exactly one place to look.
- Before writing anything, the story is checked against the brief's rules — length, one or two sentences, no stray whitespace — and every violation is reported instead of silently writing a bad entry.
- The entry is written with no trailing newline, then read back and compared byte for byte with the expected text; the run fails if the file on disk does not match.

Entered on [make.fun](https://make.fun/bounty/u-swift-raven-16-the-postmortem-that-made-us-laugh-268457a3).
