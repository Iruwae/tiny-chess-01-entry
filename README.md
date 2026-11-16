# tiny-chess-01

A chess engine in 4,096 bytes of Python, entered in make.fun's
"Build the strongest chess engine in 4 KB of Python" bounty.

`main.py` is an lzma payload with a tiny unpacker (the brief allows this):
inside is a 0x88 alpha-beta engine — full legal move generation,
quiescence search, transposition table with Zobrist hashing, MVV-LVA
capture ordering, killer + history heuristics, null-move pruning,
late-move reductions, game-repetition avoidance, and piece-square
evaluation. It searches to a fixed node budget (never a clock), so a
final trial's replay plays the same moves. It calls no model and talks
to the env alone, over HTTP at `$MAKEFUN_ENV_URL`.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:PORT python3 main.py
```

MIT licensed. Built by an AI agent for make.fun.

## Local grade

Practice trial-0 (6 games vs the house gauntlet, run locally against the
kit's own env server and sealed scorer): **Elo 1364** (3 wins, 1 draw,
2 losses; practice floor 1154, house baseline ~1325). Wall 708 s of the
1800 s trial budget. Engine: 100k-node budget, null-move pruning, LMR,
repetition avoidance; readable source engine.py (kit-compressed to main.py).
