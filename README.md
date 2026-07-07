# Market Data

Historical cryptocurrency market data organized for research.

## Bybit 5-minute data

Path layout:

```text
bybit/5m/{SYMBOL}/{spot|perpetual|funding}/{YYYY}/{MM}.csv
```

- Quote currency: USDT
- Spot files: trade OHLCV and turnover
- Perpetual files: trade OHLCV, mark-price OHLC, index-price OHLC,
  premium-index OHLC, basis, and basis percentage
- Funding files: actual funding settlements at each instrument's native
  funding interval
- Timestamps: UTC
- History: instrument launch through the generation time recorded in
  `bybit/5m/source_manifest.json`

`bybit/5m/file_index.csv` lists every monthly file, row count, byte size, and
timestamp coverage. `bybit/5m/split_summary.json` contains aggregate validation
counts.

## Bybit 1-hour open interest

Path layout:

```text
bybit/1h/{SYMBOL}/open_interest/{YYYY}/{MM}.csv
```

- Quote currency: USDT
- Contract type: USDT linear perpetuals
- Timestamps: UTC
- Open interest source: Bybit public V5 open-interest endpoint
- Coverage: available for the 2026-07-07 extension set, including BTC/ETH/SOL
  and the requested new perpetual symbols where Bybit returned OI rows

`bybit/1h/file_index.csv` lists every monthly OI file.

Basis definitions:

```text
basis = perpetual trade close - index close
basis_pct = basis / index close
```

The duplicated `SOL` in the original request was deduplicated.
