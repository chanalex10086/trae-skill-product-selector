# Profit Calculation Workflow

## Trigger Conditions
- User asks "算一下利润" / "利润测算" / "成本拆解" / "这个产品能赚多少"
- User wants detailed cost breakdown for a specific product
- User is evaluating whether a product is financially viable

## Input Requirements
Gather from user (or make reasonable estimates):
1. **Product name and specification** — what exactly is being sold
2. **Sale price** — target selling price on Amazon (must be ≥ $50 per selection rules)
3. **1688 sourcing price** — wholesale cost per unit (in CNY)
4. **Product weight** — for shipping calculation
5. **Product dimensions/CBM** — for freight calculation
6. **Fulfillment model** — FBM or FBA

## Calculation Formula

### Cost Items (8 items)

| # | Cost Item | Calculation | Currency |
|:-:|:----------|:------------|:---------|
| ① | 1688拿货价 | 1688 wholesale price | CNY |
| ② | 国内运到港口 | Estimated ¥5-20/unit based on weight | CNY |
| ③ | 海运头程 | Based on CBM × freight rate (~¥2000-3000/CBM) or weight | CNY |
| ④ | 关税 | ① × 25% | CNY |
| ⑤ | 海外仓操作费 | ¥15-30/unit (receiving + shelving) | CNY |
| ⑥ | FBM尾程运费 | Based on weight: <$10 for <5kg, $10-15 for 5-15kg, $15-25 for 15-30kg | USD |
| ⑦ | 亚马逊佣金 | Sale price × 15% | USD |
| ⑧ | 广告费 | Sale price × 10% | USD |

### Exchange Rate
Use current USD/CNY exchange rate (default: 1 USD ≈ 7.2 CNY if real-time rate unavailable).

### Profit Calculation

```
Revenue = Sale Price (USD)
Total Cost (USD) = (① + ② + ③ + ④ + ⑤) / Exchange Rate + ⑥ + ⑦ + ⑧
Net Profit = Revenue - Total Cost
Net Margin = Net Profit / Revenue × 100%
```

## Output Format

```
### 利润测算（[产品规格]，[FBM/FBA]模式）

| 成本项 | 金额 | 说明 |
|:------|:---:|:----|
| ① 1688拿货价 | **¥[price]** | [规格说明] |
| ② 国内运到港口 | ¥[price] | [说明] |
| ③ 海运头程（美西） | ¥[price] | 体积约[CBM]，重量[kg]，[拼箱/整柜] |
| ④ 关税 | ¥[price] | [税率]% |
| ⑤ 海外仓操作费 | ¥[price] | [卸货上架等] |
| ⑥ FBM尾程运费 | **$[price]** | 约¥[CNY]，[重量说明] |
| ⑦ 亚马逊佣金 | **[percentage]%** | $[amount] |
| ⑧ 广告费 | **[percentage]%** | $[amount] |

**利润核算（售价$[price]）：**

| 项目 | 金额 |
|:----|:---:|
| 💰 售价 | **$[price]** |
| 佣金（15%） | -$[amount] |
| 广告费（10%） | -$[amount] |
| 产品成本 | -¥[CNY] ≈ -$[USD] |
| 头程+关税 | -¥[CNY] ≈ -$[USD] |
| 海外仓操作 | -¥[CNY] ≈ -$[USD] |
| FBM尾程 | -$[amount] |
| **单台净利润** | **≈ $[amount]** |
| **净利率** | **≈ [percentage]%**（需≥28%） |
```

## Multi-Scenario Analysis

When a product has multiple specifications (e.g., different sizes, weights, materials), calculate profit for each scenario separately and present a comparison:

```
### 利润对比

| 规格 | 售价 | 拿货价 | 重量 | 净利润 | 净利率 | 判断 |
|:----|:---:|:-----:|:---:|:-----:|:-----:|:----:|
| [规格1] | $[price] | ¥[price] | [kg] | $[profit] | [margin]% | ✅ |
| [规格2] | $[price] | ¥[price] | [kg] | $[profit] | [margin]% | ❌ |
```

## Decision Thresholds

**选品硬性门槛：售价 ≥ $50，净利率 ≥ 28%。**

| Net Margin | Recommendation | Strategy |
|:----------|:--------------|:---------|
| ≥ 28% | ✅ 达标，推荐 | 符合毛利门槛，可推进 |
| 20-28% | ⚠️ 边缘 | 需成本优化至 28% 方可推荐 |
| < 20% | ❌ 不推荐 | 低于毛利门槛，排除 |

**Note:** Price floor $50 — products priced below $50 are auto-excluded before margin calculation.

## FBM vs FBA Comparison

When relevant, show both fulfillment models:

| Dimension | FBM | FBA |
|:----------|:----|:-----|
| Fulfillment fee | $[FBM cost] | $[FBA cost] |
| Storage fee | $[warehouse cost] | $[FBA storage] |
| Total per unit | $[total] | $[total] |
| Net profit | $[profit] | $[profit] |
| Net margin | [margin]% | [margin]% |

**Rule of thumb:** Products > 15kg or > 0.05 CBM typically favor FBM due to FBA's oversized item surcharges.
