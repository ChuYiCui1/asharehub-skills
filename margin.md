# Margin Trading — Margin & Short Selling Detail

## Background — Different from US Margin

**Margin trading and short selling exist in China but operate very differently from US markets.**

### Key differences from US margin
| | US Margin | China A-Share Margin |
|---|-----------|---------------------|
| Eligible stocks | Most stocks | **Whitelist only** (~2000 stocks) |
| Short selling | Easy, locate-based | **Restricted** — must borrow from broker's pool, often unavailable |
| Margin ratio | ~50% (Reg T) | Brokers set, typically 50-60% |
| Hot money usage | Common at retail | **Heavily used by speculators** as a leverage indicator |

### What `rzye` and `rqye` mean
- **`rzye` (融资余额, "margin buy balance")**: Total outstanding loans for buying stock. **Rising `rzye` = bullish leverage building up.** This is the most-watched metric.
- **`rqye` (融券余额, "short sell balance")**: Total outstanding short sales. Usually much smaller than `rzye` because shorting is hard.

### Why this matters for A-share investors
- **Sentiment proxy**: Aggregate `rzye` is one of the cleanest sentiment indicators. Spikes often coincide with market tops.
- **Stock-level signal**: A stock with rapidly rising `rzye` is being aggressively bought by leveraged speculators — momentum is hot but reversal risk is also high.
- **Forced selling risk**: When stocks decline, margin holders may face forced liquidation, accelerating the drop.

### Key fields explained (all in CNY)
- **`rzye` (融资余额)**: Margin buy balance (long leverage outstanding).
- **`rqye` (融券余额)**: Short sell balance.
- **`rzmre` (融资买入额)**: Margin buy volume today.
- **`rqyl` (融券余量)**: Short sell volume in shares.
- **`rzche` (融资偿还额)**: Margin loan repayment today.
- **`rqchl` / `rqmcl`**: Short cover / short sell trading volume.
- **`rzrqye` (融资融券余额)**: Combined balance = rzye + rqye in CNY.

### Caveats
- Only stocks on the official "margin trading targets" list can be margin-traded. Check if a stock is eligible before assuming margin data exists.
- Short selling supply is often limited; `rqye` may be artificially low due to lack of borrow.
- Margin balance is **end-of-day**, not intraday.


## SDK Method

```python
client.margin(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, ts_code, name, rzye, rqye, rzrqye, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.margin(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "rzye", "rqye", "rzrqye"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Stock code, e.g. `000001.SZ` |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `trade_date` | Trading date |
| `ts_code` | Stock code |
| `name` | Stock name |
| `rzye` | Margin buy balance (CNY) — total outstanding margin loans |
| `rqye` | Short sell balance (CNY) — total outstanding short positions |
| `rzmre` | Margin buy amount today (CNY) |
| `rqyl` | Short sell volume today (shares) |
| `rzche` | Margin repayment today (CNY) |
| `rqchl` | Short cover volume today (shares) |
| `rqmcl` | Short sell volume today (shares) |
| `rzrqye` | Total margin + short balance (CNY) |

## Data Coverage

- From: 2020-01-02
- Rising rzye = bullish leverage; rising rqye = bearish sentiment
- API path: `GET /v1/market/margin`
