# Datasets

Two datasets in this course. Both load directly into Power BI Desktop via the GitHub raw URL pattern (see `../CONVENTIONS.md`).

---

## AdventureWorks Sales

**File:** `AdventureWorks_Sales.xlsx`
**Raw URL:** `https://github.com/c-marq/cap2743c-power-bi-viz/raw/main/datasets/AdventureWorks_Sales.xlsx`
**Source:** Microsoft Power BI Desktop Samples — used here under Microsoft's sample data terms
**Used in:** Labs 1–10, Homeworks 1–3, Capstone

A fictional bicycle manufacturer's sales data. Already shaped as a clean star schema, which is why we use it — the prerequisite course (CAP2791C) taught you how to *build* a star schema. This course picks up with one already built and focuses on visualization, analysis, and distribution.

### Star schema (verified)

```
                   ┌──────────────────────┐
                   │     Date_data        │
                   │   (1,461 rows)       │
                   └──────────┬───────────┘
                              │
        ┌──────────────┐      │      ┌────────────────────┐
        │  Product     │      │      │  Customer          │
        │  (397 rows)  │      │      │  (18,485 rows)     │
        └──────┬───────┘      │      └─────────┬──────────┘
               │              │                │
               └──────┐       │       ┌────────┘
                      ▼       ▼       ▼
              ┌─────────────────────────────────┐
              │       Sales_data (FACT)         │
              │       121,253 rows              │
              └──┬────────┬────────┬────────┬───┘
                 │        │        │        │
        ┌────────┘        │        │        └─────────────┐
        ▼                 ▼        ▼                      ▼
┌──────────────┐  ┌──────────────┐  ┌──────────────────────────┐
│ Reseller     │  │ Sales Order  │  │   Sales Territory        │
│ (702 rows)   │  │ (degen, 121K)│  │   (11 rows)              │
└──────────────┘  └──────────────┘  └──────────────────────────┘
```

### Table reference

| Table | Rows | Type | Purpose |
|---|---|---|---|
| `Sales_data` | 121,253 | Fact | The transactions — quantity, price, cost, amount per order line |
| `Sales Order_data` | 121,253 | Degenerate dimension | Channel (Reseller / Internet) and order/line identifiers; 1:1 with fact |
| `Date_data` | 1,461 | Dimension | ~4 fiscal years, FY2018 onward |
| `Product_data` | 397 | Dimension | Bike/component/accessory/clothing products with Category → Subcategory → Model hierarchy |
| `Customer_data` | 18,485 | Dimension | End-consumer customers with geography |
| `Reseller_data` | 702 | Dimension | Wholesale resellers with business type + geography |
| `Sales Territory_data` | 11 | Dimension | Regions grouped into countries and groups (North America / Europe / Pacific) |

### Column reference

**Sales_data** (fact, 15 columns)

| Column | Type | Notes |
|---|---|---|
| SalesOrderLineKey | Integer | Unique per row, joins to Sales Order_data |
| ResellerKey | Integer | Joins to Reseller_data; `-1` when channel is Internet |
| CustomerKey | Integer | Joins to Customer_data; `-1` when channel is Reseller |
| ProductKey | Integer | Joins to Product_data |
| OrderDateKey | Integer (YYYYMMDD) | Joins to Date_data.DateKey |
| DueDateKey | Integer (YYYYMMDD) | Joins to Date_data.DateKey |
| ShipDateKey | Integer (YYYYMMDD) | Joins to Date_data.DateKey |
| SalesTerritoryKey | Integer | Joins to Sales Territory_data |
| Order Quantity | Integer | Units sold |
| Unit Price | Decimal | Price per unit before discount |
| Extended Amount | Decimal | Quantity × Unit Price |
| Unit Price Discount Pct | Decimal | 0.0 to 1.0 |
| Product Standard Cost | Decimal | Per-unit cost |
| Total Product Cost | Decimal | Quantity × Standard Cost |
| Sales Amount | Decimal | Final revenue after discount |

**Sales Order_data** (degenerate dimension, 4 columns)

| Column | Type | Notes |
|---|---|---|
| Channel | Text | "Reseller" or "Internet" |
| SalesOrderLineKey | Integer | Joins to Sales_data |
| Sales Order | Text | Order ID (e.g., "SO43659") |
| Sales Order Line | Text | Line ID (e.g., "SO43659 - 1") |

**Date_data** (dimension, 7 columns)

| Column | Type | Notes |
|---|---|---|
| DateKey | Integer (YYYYMMDD) | Primary join key |
| Date | Date | Real date type |
| Fiscal Year | Text | "FY2018", "FY2019", etc. |
| Fiscal Quarter | Text | "FY2018 Q1", etc. |
| Month | Text | "2017 Jul" |
| Full Date | Text | "2017 Jul, 01" |
| MonthKey | Integer | "201707" |

**Product_data** (dimension, 9 columns)

| Column | Type | Notes |
|---|---|---|
| ProductKey | Integer | Primary join key |
| SKU | Text | Product SKU code |
| Product | Text | Product name |
| Standard Cost | Decimal | Per-unit cost |
| Color | Text | Color name |
| List Price | Decimal | MSRP |
| Model | Text | Mid-level grouping |
| Subcategory | Text | Mid-level grouping (e.g., "Road Frames") |
| Category | Text | Top-level grouping (Bikes / Components / Clothing / Accessories) |

**Customer_data** (dimension, 7 columns)

| Column | Type | Notes |
|---|---|---|
| CustomerKey | Integer | Primary join key; `-1` is a "[Not Applicable]" placeholder for Reseller-channel sales |
| Customer ID | Text | Business identifier |
| Customer | Text | Customer name |
| City | Text | |
| State-Province | Text | |
| Country-Region | Text | |
| Postal Code | Text | |

**Reseller_data** (dimension, 8 columns)

| Column | Type | Notes |
|---|---|---|
| ResellerKey | Integer | Primary join key; `-1` is a "[Not Applicable]" placeholder for Internet-channel sales |
| Reseller ID | Text | Business identifier |
| Business Type | Text | "Specialty Bike Shop", "Value Added Reseller", "Warehouse" |
| Reseller | Text | Reseller name |
| City | Text | |
| State-Province | Text | |
| Country-Region | Text | |
| Postal Code | Text | |

**Sales Territory_data** (dimension, 4 columns)

| Column | Type | Notes |
|---|---|---|
| SalesTerritoryKey | Integer | Primary join key |
| Region | Text | (e.g., "Northwest", "Southeast") |
| Country | Text | |
| Group | Text | "North America", "Europe", "Pacific" |

### Quirks worth knowing

1. **The `[Not Applicable]` rows.** Customer_data and Reseller_data each have a row with key = -1 labeled "[Not Applicable]". This handles the channel split — an Internet sale has no reseller (ResellerKey = -1), and a Reseller sale has no end customer (CustomerKey = -1). This is a teaching moment for handling null-equivalent foreign keys in dimensional models. We treat it as a feature, not a problem.

2. **Sales Order is a degenerate dimension.** It has the same row count as the fact table (121,253) and joins 1:1. In Ch 1 we'll discuss when to keep these as separate tables vs. merge into the fact. For most labs we'll keep it separate to match the source structure.

3. **Date keys are integers, not dates.** OrderDateKey = `20170702` is the integer representation of July 2, 2017. The Date table joins on this integer key. The `Date` column on the dim table is the real date type — use that for any time-based calculations.

4. **Fiscal Year is text.** "FY2018" sorts alphabetically by default. For chronological sort in visuals, sort by `MonthKey` instead.

---

## South Florida Beach Days

**File:** `SouthFloridaBeachDays_Summer2025.csv`
**Raw URL:** `https://github.com/c-marq/cap2743c-power-bi-viz/raw/main/datasets/SouthFloridaBeachDays_Summer2025.csv`
**Source:** Synthetic dataset generated for course demo
**Used in:** Session 1 — Zero Principle demo (univariate / bivariate / multivariate)

A small, clean, single-table dataset for the Zero Principle of Data Analytics presentation. 65 logged beach visits across 8 South Florida beaches in summer 2025. Mix of continuous and categorical variables, designed to produce visible patterns in all three EDA modes.

### Column reference

| Column | Type | Range / Values |
|---|---|---|
| Visit_ID | Integer | 1–65, sequential by date |
| Visit_Date | Date | May 4 – Sep 30, 2025 |
| Beach | Text | South Beach / Mid-Beach / Sunny Isles / Bal Harbour / Crandon Park / Hollywood Beach / Fort Lauderdale Beach / Haulover |
| High_Temp_F | Decimal | ~78–94 °F |
| Water_Temp_F | Decimal | ~76–86 °F |
| UV_Index | Decimal | 4.0–12.0 |
| Wave_Height_Ft | Decimal | 0.5–4.5 ft |
| Hours_Spent | Decimal | ~1.0–8.0 hours |
| Group_Size | Integer | 1–8 |
| Total_Spent_USD | Decimal | ~$8–$220 |
| Crowd_Level | Text | Low / Medium / High |
| Activity | Text | Sunbathing / Swimming / Surfing / Snorkeling / Picnic / Volleyball / Reading |
| Satisfaction | Decimal | 1.0–10.0 |

### Patterns baked in

- **Satisfaction peaks at temperatures around 86–88 °F.** Both colder (<82 °F) and hotter (>90 °F) days score lower. Clean inverted-U when plotted as a scatter.
- **Crowd level inversely correlates with satisfaction.** Low (≈8.9) → Medium (≈7.9) → High (≈7.0).
- **Beach rankings vary.** Crandon Park (≈9.8) and Sunny Isles (≈9.1) trend highest. South Beach (≈6.0) trends lowest — the visible outlier.
- **Activity-wave-height stratification.** Surfers cluster at 2.1–4.4 ft waves; swimmers cluster at 0.9–1.8 ft. Clean multivariate signal when colored by activity.

This is a clean dataset by design — no missing values, no malformed rows. Data cleaning was covered in CAP2791C; this dataset is for exploring, not cleaning.
