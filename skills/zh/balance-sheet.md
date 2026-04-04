# 资产负债表

## SDK 方法

```python
client.balance_sheet(ts_code=None, start_date=None, end_date=None, limit=20, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.balance_sheet(ts_code="000001.SZ", limit=3)
print(df[["end_date", "total_assets", "total_liab"]])
```

## 参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `ts_code` | str | None | 股票代码 |
| `start_date` | str | None | 报告期起始，YYYY-MM-DD |
| `end_date` | str | None | 报告期截止，YYYY-MM-DD |
| `limit` | int | 20 | 返回行数，最大 200 |
| `offset` | int | 0 | 分页偏移量 |

## 返回字段

| 分类 | 字段 |
|------|------|
| **流动资产** | `total_cur_assets`, `money_cap`, `accounts_receiv`, `inventories` |
| **非流动资产** | `total_nca`, `fix_assets`, `intan_assets`, `goodwill`, `lt_eqt_invest` |
| **资产合计** | `total_assets` |
| **流动负债** | `total_cur_liab`, `st_borr`, `acct_payable` |
| **非流动负债** | `total_ncl`, `lt_borr`, `bond_payable` |
| **负债合计** | `total_liab` |
| **所有者权益** | `total_hldr_eqy_exc_min_int`, `minority_int` |

## 备注

- 金额单位：元（CNY）
- API 路径：`GET /v1/financials/balance-sheet`
