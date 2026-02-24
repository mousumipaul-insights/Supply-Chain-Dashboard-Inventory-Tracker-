# 📦 Supply Chain Dashboard & Inventory Tracker



> **Personal Project · January 2026 · Mousumi Paul**

An end-to-end inventory management system combining **Excel (Solver + Scenario Manager)**, **SQL databases (PostgreSQL + MySQL)**, **Python**, and **live BI dashboards (Power BI + Tableau)** to track real-time stock levels, compute optimal order quantities, and automate low-stock alerts across 5 product categories — reducing simulated excess holding costs by **22%** and eliminating stockout incidents.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Key Results](#-key-results)
- [Project Structure](#-project-structure)
- [Tech Stack](#-tech-stack)
- [Excel Workbook](#-excel-workbook)
- [SQL Database Layer](#-sql-database-layer)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Tableau Dashboard](#-tableau-dashboard)
- [Python Modules](#-python-modules)
- [Setup & Usage](#-setup--usage)

---

## 🔍 Project Overview

This project simulates a production-grade supply chain analytics system for a retail business managing **5 product categories** — Electronics, Apparel, Home & Kitchen, Sports & Outdoors, and Beauty & Health.

**Three core problems solved:**

**1. Real-Time Inventory Tracking** — Live stock levels connected to a PostgreSQL/MySQL backend, with automatic alert status (🔴 Critical / 🟠 Reorder / 🟡 Excess / 🟢 Healthy) triggered by EOQ and reorder point thresholds.

**2. Inventory Optimization** — EOQ, Safety Stock, and Reorder Points calculated via both Excel Solver (interactive) and Python (automated pipeline), reducing simulated excess holding costs by **22%**.

**3. BI Dashboard Integration** — Power BI and Tableau dashboards connected directly to SQL views via DirectQuery/JDBC, with automated low-stock alert feeds and supplier performance scorecards.

---

## 🏆 Key Results

| Metric | Result |
|--------|--------|
| 💰 Excess Holding Cost Reduction | **~22%** vs unoptimized baseline |
| 🚫 Stockout Incidents | **0** (eliminated via proactive ROP alerts) |
| 📦 Products Optimized | **5 / 5** categories |
| ⚠️ Automated Alerts | **Live** in Power BI + Tableau + Excel |
| 🗄️ SQL Views Created | **5** (PostgreSQL + MySQL) |
| 📊 Excel Live Formulas | **129 (0 errors)** |
| 🔄 Stored Procedures | **5** (snapshot, alerts, PO management) |

### Inventory Optimization by Category

| Category | EOQ (units) | Safety Stock | Reorder Point | Status |
|----------|-------------|--------------|---------------|--------|
| Electronics | 183 | 90 | 428 | 🟠 Reorder |
| Apparel | 242 | 74 | 355 | 🟢 Healthy |
| Home & Kitchen | 200 | 56 | 291 | 🔴 Critical |
| Sports & Outdoors | 204 | 103 | 450 | 🔴 Critical |
| Beauty & Health | 330 | 49 | 326 | 🟢 Healthy |

---

## 📁 Project Structure

```
supply-chain-dashboard/
│
├── 📊 excel/
│   └── SupplyChain_Dashboard_Tracker.xlsx    ← 7-sheet model · 129 live formulas · 0 errors
│
├── 🗄️  sql/
│   ├── postgresql/
│   │   ├── schema.sql                         ← DDL: tables, indexes, triggers, generated cols
│   │   └── seed_data.sql                      ← Sample data for all 5 products
│   ├── mysql/
│   │   ├── schema.sql                         ← MySQL 8.0 compatible DDL
│   │   ├── seed_data.sql                      ← MySQL seed inserts
│   │   └── views.sql                          ← MySQL-compatible view definitions
│   ├── views/
│   │   └── vw_inventory_dashboard.sql         ← 5 SQL views: dashboard, alerts, KPIs, suppliers
│   ├── procedures/
│   │   └── sp_inventory_procedures.sql        ← 5 stored procedures
│   └── queries/
│       ├── powerbi_queries.sql                ← 7 DirectQuery queries for Power BI
│       └── tableau_queries.sql                ← 4 Custom SQL queries for Tableau
│
├── 📈 powerbi/
│   └── dax_measures.md                        ← 25+ DAX measures documented
│
├── 📉 tableau/
│   └── tableau_connection_guide.md            ← JDBC setup, calculated fields, layout guide
│
├── 🐍 src/
│   ├── inventory_engine.py                    ← EOQ / Safety Stock / ROP engine + cost curves
│   ├── alert_engine.py                        ← Low-stock alert pipeline + email/log output
│   ├── sql_connector.py                       ← PostgreSQL + MySQL connection helpers
│   └── utils.py                               ← Formatting, export, reporting helpers
│
├── 📓 notebooks/
│   ├── 01_database_setup.ipynb                ← Schema creation, seed data, connection tests
│   ├── 02_inventory_optimization.ipynb        ← EOQ/ROP/SS analysis + cost savings
│   ├── 03_alert_engine.ipynb                  ← Alert generation, thresholds, output
│   └── 04_sql_integration.ipynb              ← SQL ↔ Python integration, view queries
│
├── 📂 data/
│   ├── raw/
│   │   ├── sales_data_2024.csv                ← 60-row monthly sales (5 categories × 12 months)
│   │   ├── inventory_params.csv               ← EOQ model inputs per product
│   │   └── supplier_data.csv                  ← Supplier lead times and OTD rates
│   └── processed/                             ← Auto-generated by notebooks
│
├── 📄 docs/
│   └── methodology.md                         ← EOQ formulas, SQL architecture, alert logic
│
├── requirements.txt
├── .env.example                               ← DB credentials template
├── .gitignore
└── README.md
```

---

## 🛠 Tech Stack

| Layer | Tool | Purpose |
|-------|------|---------|
| **Spreadsheet** | Excel (Solver, Scenario Manager) | Interactive EOQ optimization, 3-scenario model, live alert dashboard |
| **Database** | PostgreSQL 15 | Primary backend: star schema, generated columns, stored procedures |
| **Database** | MySQL 8.0 | Alternative backend: compatible DDL and views |
| **BI – Microsoft** | Power BI (DAX) | DirectQuery dashboard: KPI cards, demand trends, alert feed |
| **BI – Tableau** | Tableau Desktop | Custom SQL dashboards: EOQ curves, supplier scorecard, heat maps |
| **Language** | Python 3.10+ | Inventory engine, alert pipeline, SQL connector, automation |
| **Libraries** | pandas, numpy, sqlalchemy, psycopg2, matplotlib | Data processing and visualization |
| **Notebooks** | Jupyter | Step-by-step analysis and database integration |

---

## 📊 Excel Workbook

`SupplyChain_Dashboard_Tracker.xlsx` — **7 sheets, 129 live formulas, 0 errors**

| Sheet | Description |
|-------|-------------|
| `Inventory_Tracker` | Real-time stock entry · EOQ/ROP/SS auto-computed · alert status auto-triggers |
| `EOQ_Solver_Model` | Excel Solver optimization + 3-scenario Scenario Manager (Base / High-Demand / Cost-Optimized) |
| `Demand_Trends` | 12-month sales · MoM growth % · peak month detection · trend line chart |
| `Supplier_LeadTime` | Supplier names · agreed vs actual lead times · OTD % · star ratings |
| `SQL_Export_Preview` | Simulated output of `vw_inventory_dashboard` SQL view with embedded query |
| `KPI_Dashboard` | Live KPI cards pulling from Inventory_Tracker: costs, alerts, days of supply |
| `Guide` | Color legend · sheet index · formula reference · SQL connection notes |

### Color Coding Convention

| Color | Meaning |
|-------|---------|
| 🔵 Blue text | Hardcoded inputs — safe to edit |
| ⚫ Black text | Formula outputs — do not modify |
| 🟢 Green text | Cross-sheet formula links |
| 🟡 Yellow background | Key inputs requiring regular updates |
| Teal highlight | EOQ output values |
| Green highlight | Safety stock values |
| Blue highlight | Reorder point values |

### Excel Solver Setup
1. Open `EOQ_Solver_Model` sheet
2. Go to **Data → Solver**
3. Set Objective: Total Cost column → **Min**
4. Variable Cells: Order Quantity column
5. Constraints: Order Qty ≥ Safety Stock
6. Method: **GRG Nonlinear** → Solve

---

## 🗄️ SQL Database Layer

### Star Schema

```
dim_products ──────┐
dim_suppliers ──────┤──▶ fact_inventory      ──▶ vw_inventory_dashboard
dim_date ───────────┘──▶ fact_sales          ──▶ vw_sales_trend
                     ──▶ fact_purchase_orders ──▶ vw_supplier_performance
                                              ──▶ vw_low_stock_alerts
                                              ──▶ vw_kpi_summary
```

### SQL Views

| View | Used By | Description |
|------|---------|-------------|
| `vw_inventory_dashboard` | Power BI, Tableau | Main metrics: EOQ, ROP, SS, alert status, costs |
| `vw_sales_trend` | Power BI, Tableau | Monthly sales with MoM growth via window functions |
| `vw_supplier_performance` | Tableau | OTD %, spend, lead time variance, supplier grade |
| `vw_low_stock_alerts` | Power BI alert feed | Real-time prioritized alert queue |
| `vw_kpi_summary` | Power BI KPI cards | Aggregated headline metrics |

### Stored Procedures

| Procedure | Purpose |
|-----------|---------|
| `sp_refresh_inventory_snapshot` | Daily snapshot: auto-computes stock from sales + PO receipts |
| `sp_generate_alert_report` | Prints prioritized alert report to console/log |
| `sp_place_purchase_order` | Creates new PO at EOQ quantity |
| `sp_receive_purchase_order` | Marks PO received, triggers stock update |
| `sp_monthly_cost_report` | Monthly holding + ordering cost report by product |

### Key Formula Logic (SQL Generated Columns)

```sql
-- EOQ
ROUND(SQRT(2 × annual_demand × ordering_cost / holding_cost_per_unit))

-- Safety Stock
ROUND(z_score × demand_std_dev × SQRT(lead_time_days / 30))

-- Reorder Point
ROUND((annual_demand / working_days) × lead_time_days + safety_stock)

-- Alert Status (PostgreSQL Generated Column)
CASE
    WHEN current_stock < safety_stock              THEN 'CRITICAL'
    WHEN current_stock < reorder_point             THEN 'REORDER'
    WHEN current_stock > (reorder_point + eoq_qty) THEN 'EXCESS'
    ELSE 'HEALTHY'
END
```

---

## ⚡ Power BI Dashboard

Connected to PostgreSQL via **DirectQuery** using queries from `sql/queries/powerbi_queries.sql`. All 25+ DAX measures documented in `powerbi/dax_measures.md`.

**5 Dashboard Pages:**

| Page | Visuals |
|------|---------|
| Executive Overview | KPI cards · demand trend · low-stock alert banner |
| Inventory Health | Stock vs ROP vs Safety Stock bars · conditional-format alert table |
| Demand Trends | Monthly line chart · MoM growth waterfall · rolling 3M/6M average |
| Supplier Scorecard | Lead time variance bar · OTD gauge · spend treemap |
| Purchase Pipeline | Open PO table · expected arrival timeline · inbound cost total |

**Key DAX Highlights:**
- `[Low Stock Alert Message]` — dynamic emoji alert string driven by SQL data
- `[Alert Status Color]` — hex color measure for conditional table formatting
- `[Rolling 3M Avg Demand]` — DATESINPERIOD window lookback
- `[Inventory Health Score]` — % of products currently in healthy state

---

## 📉 Tableau Dashboard

Connected via **Custom SQL** using queries from `sql/queries/tableau_queries.sql`. Full setup in `tableau/tableau_connection_guide.md`.

**4 Dashboard Sheets:**

| Sheet | Visualization |
|-------|--------------|
| Inventory Health Map | Heat map: stock level vs reorder threshold per product |
| EOQ Cost Curve | Dual-axis: holding cost + ordering cost + total cost vs order qty |
| Demand Trend | Line chart: actual units + rolling average overlay |
| Supplier Scorecard | Bar chart: OTD % by supplier, colored by performance band |

---

## 🐍 Python Modules

| Module | Key Functions |
|--------|--------------|
| `src/inventory_engine.py` | `eoq()`, `safety_stock()`, `reorder_point()`, `run_optimization()`, `plot_eoq_curve()` |
| `src/alert_engine.py` | `check_stock_levels()`, `generate_alert_report()`, `send_email_alert()`, `log_alerts()` |
| `src/sql_connector.py` | `get_pg_engine()`, `get_mysql_engine()`, `run_query()`, `upsert_inventory()` |
| `src/utils.py` | `fmt_inr()`, `fmt_pct()`, `save_csv()`, `combined_report()` |

---

## ⚙️ Setup & Usage

### 1. Clone & Install

```bash
git clone https://github.com/mousumi-paul/supply-chain-dashboard.git
cd supply-chain-dashboard
pip install -r requirements.txt
```

### 2. Configure Database Credentials

```bash
cp .env.example .env
# Edit .env with your PostgreSQL / MySQL credentials
```

```env
PG_HOST=localhost
PG_PORT=5432
PG_DB=supply_chain_db
PG_USER=your_user
PG_PASS=your_password

MYSQL_HOST=localhost
MYSQL_PORT=3306
MYSQL_DB=supply_chain_db
MYSQL_USER=your_user
MYSQL_PASS=your_password
```

### 3. Set Up PostgreSQL

```bash
psql -U your_user -f sql/postgresql/schema.sql
psql -U your_user -d supply_chain_db -f sql/postgresql/seed_data.sql
psql -U your_user -d supply_chain_db -f sql/views/vw_inventory_dashboard.sql
psql -U your_user -d supply_chain_db -f sql/procedures/sp_inventory_procedures.sql
```

### 4. Set Up MySQL (alternative)

```bash
mysql -u your_user -p < sql/mysql/schema.sql
mysql -u your_user -p supply_chain_db < sql/mysql/seed_data.sql
mysql -u your_user -p supply_chain_db < sql/mysql/views.sql
```

### 5. Run Jupyter Notebooks

```bash
jupyter notebook notebooks/01_database_setup.ipynb        # DB connection + schema test
jupyter notebook notebooks/02_inventory_optimization.ipynb    # EOQ/ROP/SS + cost savings
jupyter notebook notebooks/03_alert_engine.ipynb           # Alert pipeline
jupyter notebook notebooks/04_sql_integration.ipynb        # SQL ↔ Python integration
```

### 6. Run Alert Engine Directly

```bash
python src/alert_engine.py
# Prints prioritized alert report; set EMAIL_ALERTS=true in .env for email output
```

### 7. Use the Excel Workbook

1. Open `excel/SupplyChain_Dashboard_Tracker.xlsx`
2. Go to `Inventory_Tracker` → update **yellow cells** (Column L: Current Stock)
3. `KPI_Dashboard` and `SQL_Export_Preview` sheets refresh automatically
4. **Solver:** `EOQ_Solver_Model` → Data → Solver → Solve
5. **Scenario Manager:** `EOQ_Solver_Model` → Data → What-If Analysis → Scenario Manager

### 8. Connect Power BI

1. **Get Data → PostgreSQL** → Server: `localhost:5432` | DB: `supply_chain_db`
2. Choose **DirectQuery** mode
3. Import each query from `sql/queries/powerbi_queries.sql` as a named query
4. Add all DAX measures from `powerbi/dax_measures.md`
5. Apply `[Alert Status Color]` to table conditional formatting

### 9. Connect Tableau

See `tableau/tableau_connection_guide.md` for full instructions:
1. Connect → PostgreSQL (JDBC) or Other Databases (ODBC)
2. Use Custom SQL from `sql/queries/tableau_queries.sql`
3. Add calculated fields for alert colors and supplier performance bands

---

## 📄 Documentation

Full methodology, schema design, and formula derivations are in [`docs/methodology.md`](docs/methodology.md).

---

## 📬 Contact

**Mousumi Paul**  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/mousumi-paul)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/mousumi-paul)
