# Concepts — Theme/Concept Sector Indices

## Background — China's Theme-Driven Market

**"Concepts" (概念) are theme-based stock groupings unique to China's retail-driven market.** Unlike traditional industry classifications (e.g. SWS, GICS), concepts reflect **trading themes and narratives** that drive A-share rotation.

### Concept vs Industry
| | Industry Classification | Concept |
|---|------------------------|---------|
| Source | Official (Shenwan/CSRC) | Compiled by data vendors (东方财富/同花顺) |
| Stability | Long-term, rarely changes | Created/retired based on market themes |
| Examples | Banking, Pharma, Retail | "AI Concept", "BRICS Concept", "Huawei Mate Phone Concept", "ChatGPT Concept" |
| Stock-to-group | One industry per stock | One stock can be in many concepts |

### Why concepts matter in A-shares
- **Driver of rotation**: A-share rallies often go through "concept rotation" — money flows from one hot theme to the next on weekly cycles.
- **News-driven**: A new policy announcement or product launch can spawn a new concept and rally its members 20-50% in days.
- **Retail attention**: Retail investors trade concepts, not fundamentals. Tracking which concepts are heating up reveals where retail money flows.

### Common concept categories
- **Tech narratives**: AI, ChatGPT, robots, semiconductors, autonomous driving
- **Policy themes**: Belt & Road, BRICS, common prosperity, state-owned enterprise reform
- **Supply chain**: Specific company supply chains (e.g. "Apple Chain", "Tesla Chain")
- **Macro events**: Hurricane, pandemic, Russian-Ukraine war, etc.

### Key fields explained
- **`ts_code`**: Concept index code (e.g. `BK0425.DC` from Eastmoney).
- **`name`**: Concept name in Chinese (e.g. "ChatGPT概念").
- **`leading`**: Today's leading constituent stock.
- **`pct_change`**: Concept index daily return.
- **`up_num` / `down_num`**: Number of constituent stocks rising / falling.
- **`level`**: Concept hierarchy level.

### Caveats
- Concept membership is **vendor-defined and subjective**. Same theme may have different members in different vendors' data.
- Concepts are **not fundamentally pure** — a "robot concept" stock may derive only 5% revenue from robotics.
- Hot concepts tend to be **mean-reverting** after the narrative peaks.


## SDK Method

```python
client.concepts(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, trade_date, name, pct_change, leading, etc. Returns empty DataFrame if no data.

## Example

```python
df = client.concepts(limit=3)
print(df[["trade_date", "name", "pct_change", "leading"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `ts_code` | str | None | Concept code, e.g. `BK0425.DC` |
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 5000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `ts_code` | Concept index code (e.g. BK0425.DC) |
| `trade_date` | Trading date |
| `name` | Concept name (e.g. AI, New Energy, Semiconductors) |
| `leading` | Leading stock name |
| `leading_code` | Leading stock code |
| `pct_change` | Daily return % |
| `leading_pct` | Leading stock return % |
| `total_mv` | Total market value (10k CNY) |
| `turnover_rate` | Turnover rate % |
| `up_num` | Number of rising stocks |
| `down_num` | Number of falling stocks |
| `idx_type` | Index type |
| `level` | Index level |

## Data Coverage

- From: 2025-04-01
- Records: 109K+, 508 concept indices
- API path: `GET /v1/market/concepts`
