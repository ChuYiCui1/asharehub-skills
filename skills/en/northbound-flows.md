# Northbound Flows — Stock Connect Capital Flows

## SDK Method

```python
client.northbound_flows(start_date=None, end_date=None, limit=100, offset=0)
```

## Returns

`pd.DataFrame` — columns: trade_date, hgt_ss, hgt_sz, ggt_ss, ggt_sz, north_money, south_money. Returns empty DataFrame if no data.

## Example

```python
df = client.northbound_flows(limit=3)
print(df[["trade_date", "north_money", "south_money"]])
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `start_date` | str | None | Start date, YYYY-MM-DD |
| `end_date` | str | None | End date, YYYY-MM-DD |
| `limit` | int | 100 | Max rows, up to 2000 |
| `offset` | int | 0 | Pagination offset |

## Response Fields

| Field | Description |
|-------|-------------|
| `trade_date` | Trading date |
| `hgt_ss`, `hgt_sz` | Shanghai / Shenzhen northbound (millions CNY) |
| `ggt_ss`, `ggt_sz` | HK southbound via Shanghai / Shenzhen (millions CNY) |
| `north_money` | Total northbound net inflow (millions CNY) — positive = net buying |
| `south_money` | Total southbound net inflow (millions CNY) |

## Data Coverage

- From: 2014-11-17
- One record per trading day
- Key indicator of foreign investor sentiment toward A-shares
- API path: `GET /v1/flows/northbound`
