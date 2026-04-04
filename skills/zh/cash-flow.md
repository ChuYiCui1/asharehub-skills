# 现金流量表

## SDK 方法

```python
client.cash_flow(ts_code=None, start_date=None, end_date=None, limit=20, offset=0)
```

## 返回类型

`pd.DataFrame` — 数值列为 `float64`。无数据时返回空 DataFrame。

## 示例

```python
df = client.cash_flow(ts_code="000001.SZ", limit=3)
print(df[["end_date", "n_cashflow_act", "free_cashflow"]])
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
| **经营活动** | `c_fr_sale_sg`, `c_pay_goods_purch_serv_rec`, `n_cashflow_act` |
| **投资活动** | `c_pay_acq_const_fix_intang_oasset`, `n_cashflow_inv_act` |
| **筹资活动** | `c_fr_borr`, `c_pay_dist_dpcp_int_exp`, `n_cash_flows_fnc_act` |
| **汇总** | `n_incr_cash_cash_equ`, `c_cash_equ_end_period` |
| **衍生** | `free_cashflow`（自由现金流 = 经营现金流 - 资本支出） |

## 备注

- 金额单位：元（CNY）
- API 路径：`GET /v1/financials/cash-flow`
