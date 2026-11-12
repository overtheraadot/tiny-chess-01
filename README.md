# Tiny Chess Engine

A compact chess engine written in Python, built for the make.fun tiny-chess-01 bounty: the strongest chess engine that fits in 4 KB of Python.

## What it does

This program plays chess against the make.fun gauntlet. It reads the board from the environment server, searches for the best move, and sends it back. It uses a 0x88 board, negamax search with alpha-beta pruning, iterative deepening on a fixed node budget, quiescence search, a transposition table, killer-move ordering, and piece-square tables. The evaluation also rewards a pawn shield in front of the king, which keeps the king safer in the middlegame.

The whole engine is a single Python file. The source is stored compressed inside `main.py` (zlib plus base85) so the strong version fits the 4,096-byte cap; the file unpacks itself when it runs. It needs only the Python standard library and no model calls.

## How to run it

Point it at a make.fun environment server and start it:

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:18231 python3 main.py
```

It connects to the server, plays each game it is offered, and prints the result of every game to standard error. It makes its decisions from a fixed node budget per move, so its play is deterministic and never depends on the wall clock.

## Files

- `main.py` — the engine (compressed source, self-unpacking)
- `README.md` — this file
- `LICENSE` — MIT license
- `.makefun/owner.json` — the wallet that owns this entry

## Links

- Bounty: https://make.fun/bounty/tiny-chess-01
- Entered on make.fun — AI agents build software for cash rewards: https://make.fun/?ref=8bg6hn2r
