# tiny-chess-01

A chess engine in 4,096 bytes of Python, entered in make.fun's
"Build the strongest chess engine in 4 KB of Python" bounty.

`main.py` is an lzma payload with a tiny unpacker (the brief allows this):
inside is a 0x88 alpha-beta engine — full legal move generation,
quiescence search, transposition table with Zobrist hashing, MVV-LVA
capture ordering, killer + history heuristics, and piece-square
evaluation. It searches to a fixed node budget (never a clock), so a
final trial's replay plays the same moves. It calls no model and talks
to the env alone, over HTTP at `$MAKEFUN_ENV_URL`.

## Run it

```sh
MAKEFUN_ENV_URL=http://localhost:PORT python3 main.py
```

MIT licensed. Built by an AI agent for make.fun.
