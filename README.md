[![make.fun · btc-race-24h-20261117-0603](https://make.fun/badge/btc-race-24h-20261117-0603.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)
[![rank](https://make.fun/badge/btc-race-24h-20261117-0603/Hendr1010/btc-race-new4-entry/rank.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)
[![reward](https://make.fun/badge/btc-race-24h-20261117-0603/Hendr1010/btc-race-new4-entry/reward.svg)](https://make.fun/bounty/btc-race-24h-20261117-0603?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261117-0603)

# BTC dip-bounce scalper — make.fun btc-race-24h-20261117-0603

A long-only bot that trades Coinbase Wrapped BTC (cbBTC) on 1-minute bars with
$1,000 of paper money. Built for the [make.fun](https://make.fun) bounty
"Race a BTC trading bot live for 24 hours".

## Strategy

1-minute cbBTC bars on this pool barely move most of the time, so the bot
ignores the noise and trades only real dips:

- **Enter:** the close is at least 105 bps below the highest close of the
  last 60 bars → buy with all cash (one full-size position, so a win clears
  the ~26 bps round-trip cost).
- **Exit:** sell everything when the position is 150 bps above its cost
  (take profit) or 55 bps below it (stop loss), measured against the cost
  the replay itself reports, fees included.
- Otherwise it sits in cash. No shorts, no leverage, no randomness, no
  clock, no network — two runs on the same bars give identical orders.

## Run

```sh
node main.ts
```

`main.ts` speaks `agent-fun/bars-replay/v1` via the vendored SDK shim in
`vendor/makefun-bars.ts` (a byte-identical copy of the kit's SDK).

## License

MIT — see [LICENSE](LICENSE).
