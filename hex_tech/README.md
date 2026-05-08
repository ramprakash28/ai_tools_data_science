# Hex

## Overview

**Hex** is an AI-native collaborative data workspace that combines notebooks, SQL, Python, and no-code app building in one platform. It is designed for data teams who want to go from raw data to shareable insights without switching tools. Hex's built-in AI (Magic) can clean data, write SQL/Python, perform EDA, and build visualizations through natural language prompts.

- **Made by:** Hex Technologies
- **Type:** Cloud-based AI data workspace
- **Website:** [hex.tech](https://hex.tech)
- **Pricing:** Freemium — free personal tier; paid plans for teams

---

## Capabilities

- **AI-Powered Analysis (Hex Magic)** — Prompt the AI in plain English to clean data, write SQL or Python, find insights, or build charts. The AI explains its reasoning and shows every transformation it applies.
- **Notebook + SQL in One** — Mix SQL cells and Python cells in the same project. Query a database with SQL, pull results into a dataframe, and continue with Python — no context switching.
- **Non-Destructive Data Transformations** — All AI-applied transformations operate on a copy of the dataset, keeping the original data untouched. Every change is logged and reversible.
- **App Builder** — Convert any notebook into an interactive data app with charts, filters, dropdowns, and tables. Publish and share with stakeholders who don't need to see the code.
- **Data Profiling & EDA** — Automatically generate shape, dtype, missing value, and duplicate summaries for any dataset. Identify outliers and data quality issues instantly.
- **Chart Builder (No-Code)** — Build charts visually by dragging columns to axes. Supports bar, line, pie, scatter, histogram, and more without writing any plotting code.
- **Real-Time Collaboration** — Multiple users can work in the same project simultaneously. Leave comments, review changes, and collaborate like a shared document.
- **Version History** — Every change is tracked. Roll back to any previous state of the notebook.
- **Data Source Integrations** — Connect to Snowflake, BigQuery, Redshift, PostgreSQL, MySQL, dbt, and more.
- **Scheduled Runs** — Automate notebook execution on a schedule and refresh published apps with fresh data.
- **Pending Changes Review** — Before any transformation is committed, Hex shows a diff of what will change and asks for confirmation. Undo is always available.

---

## Use Cases

### 1. AI-Assisted Data Cleaning
Upload a raw dataset and prompt Hex Magic to identify and fix data quality issues — blank values, wrong data types, inconsistent encodings — without writing a single line of code. Every fix is shown as a transparent, reviewable transformation.

### 2. Exploratory Data Analysis (EDA)
Ask Hex to profile a dataset, summarize distributions, flag anomalies, and generate initial charts. The AI produces a structured summary with data shape, column types, and notable issues in seconds.

### 3. SQL + Python Hybrid Workflows
Write SQL to query and filter data from a connected warehouse, then pass results directly into Python for modeling, visualization, or further transformation — all in the same notebook.

### 4. Business Intelligence Apps
Use the App Builder to turn a notebook into a polished, interactive dashboard. Non-technical stakeholders can filter, explore, and interact with the data without seeing code.

### 5. Customer Churn Analysis *(this repo's example)*
Used to analyze the **IBM Telco Customer Churn dataset** (7,043 rows, 21 columns). Hex Magic was prompted to:
- Profile the dataset and identify data quality issues
- Fix `TotalCharges` (blank string → numeric, 11 nulls where `tenure = 0`)
- Re-encode `SeniorCitizen` from 0/1 integer → `Yes/No` categorical
- Flag service add-on columns using `"No internet service"` as a spurious third category
- Build a Churn Distribution pie chart revealing ~27% churn rate (1,869 of 7,043 customers)

All transformations were applied non-destructively on `df_clean`, with the AI explaining each step and offering undo before committing.

> See [`examples/`](./examples/) for the dataset and [`screenshots/`](./screenshots/) for visuals from this project.

---

## Pricing

| Plan | Price | Key Details |
|---|---|---|
| Free | $0 | 1 user, unlimited projects, community support |
| Team | From $24/user/month | Shared workspaces, scheduled runs, SSO |
| Enterprise | Custom | Advanced security, custom compute, SLAs |

---

## Links

- Website: [hex.tech](https://hex.tech)
- Documentation: [learn.hex.tech](https://learn.hex.tech)
- Hex Magic (AI): [hex.tech/magic](https://hex.tech/magic)
- Blog: [hex.tech/blog](https://hex.tech/blog)
