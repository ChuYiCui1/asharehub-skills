# Money Flow — Individual Stock Money Flow

## SDK Method

```python
client.moneyflow(ts_code=None, start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: ts_code, trade_date, buy/sell amounts by order size, net_mf_amount. Returns empty DataFrame if no data.

## Example

```python
df = client.moneyflow(ts_code="000001.SZ", limit=3)
print(df[["trade_date", "net_mf_amount", "buy_elg_amount"]])
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
| `ts_code` | Stock code |
| `trade_date` | Trading date |
| `buy_sm_vol`, `buy_sm_amount` | Small order (<50K) buy volume/amount |
| `sell_sm_vol`, `sell_sm_amount` | Small order sell volume/amount |
| `buy_md_vol`, `buy_md_amount` | Medium order (50K-200K) buy volume/amount |
| `sell_md_vol`, `sell_md_amount` | Medium order sell volume/amount |
| `buy_lg_vol`, `buy_lg_amount` | Large order (200K-1M) buy volume/amount |
| `sell_lg_vol`, `sell_lg_amount` | Large order sell volume/amount |
| `buy_elg_vol`, `buy_elg_amount` | Extra-large order (>=1M) buy volume/amount |
| `sell_elg_vol`, `sell_elg_amount` | Extra-large order sell volume/amount |
| `net_mf_vol` | Net money flow volume (lots) |
| `net_mf_amount` | Net money flow amount (10k CNY). Positive = net buying |

## Data Coverage

- From: 2020-01-02
- Records: 5.7M+
- Amounts in 10k CNY, volumes in lots
- API path: `GET /v1/flows/moneyflow`
