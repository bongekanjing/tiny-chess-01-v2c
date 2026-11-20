# tiny-chess-01-v2c

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/bongekanjing/tiny-chess-01-v2c/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/bongekanjing/tiny-chess-01-v2c/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in at most 4,096 bytes of Python (this entry: 3,722 bytes, pure standard library only). It plays the house gauntlet through the env at `MAKEFUN_ENV_URL` (POST `/game`, `/move`, `/resign`) and exits when every game is over.

The engine: a 0x88 board with a full legal move generator (castling, en passant, promotion, check detection), PVS alpha-beta with a transposition table, null-move pruning, check extensions, quiescence (captures and check replies; a mated position scores as mate, never as a stand-pat evaluation), killer moves, and a tapered evaluation (material, centrality, pawn advance, passed / isolated / doubled pawns, bishop pair, king safety by phase). Search is iterative deepening to a fixed node budget of 50,000 nodes per move (never a clock), so play is fully deterministic and replays move for move.

Local practice-trial results (this version): trial 0: 2 wins, 1 draw, 3 losses (~1191 Elo); trial 1: 1 win, 3 draws, 2 losses (~1191 Elo); combined 5.0/12, better than the previous 40,000-node version (4.5/12).

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:PORT python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=yg9xmt6c&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
