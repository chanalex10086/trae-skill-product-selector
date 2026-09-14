# TRAE Skill - Amazon 产品经理选品器

> Cross-border e-commerce Amazon product development assistant for TRAE

## Overview

This TRAE skill assists cross-border e-commerce sellers in Amazon US market product development. It covers four core workflows:

- **Product Recommendation** (选品推荐) — Generate 3-5 ranked product recommendations with blue ocean criteria
- **Category Analysis** (品类分析) — Evaluate whether a specific category is viable on Amazon with go/no-go verdict
- **Profit Calculation** (利润测算) — Detailed 8-item cost breakdown and net margin analysis
- **Product Specification** (产品需求书) — Complete spec document for factory communication

## Skill Structure

```
.
├── SKILL.md                              # Main skill definition and routing
└── references/
    ├── product-recommendation.md         # Product recommendation workflow
    ├── category-analysis.md              # Category analysis workflow
    ├── profit-calculation.md             # Profit calculation workflow
    └── product-specification.md          # Product specification workflow
```

## Key Features

- **Blue ocean selection** — Target products with monthly sales 100-800, avoiding red ocean categories
- **FBM priority** — Large/heavy items favor FBM due to high FBA fees
- **1688 sourcing** — All cost estimates use 1688 wholesale prices as baseline
- **Fast launch signal** — Prioritize categories where new ASINs can get first orders quickly
- **Data-driven decisions** — Every recommendation includes price, cost, sales, margin, and competition assessment

## Installation

Copy the `SKILL.md` and `references/` directory into your TRAE skills directory:

```
<data>/user/skills/trae-skill-product-selector/
├── SKILL.md
└── references/
    ├── product-recommendation.md
    ├── category-analysis.md
    ├── profit-calculation.md
    └── product-specification.md
```

## Usage

Invoke the skill when you need to:
- Find new product directions for Amazon US market
- Analyze whether a specific category is viable
- Calculate profit margins for a product
- Generate a product specification document

## License

MIT
