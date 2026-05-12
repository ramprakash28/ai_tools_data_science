# Julius AI

## Overview

**Julius AI** is a conversational AI data analyst that lets you upload datasets and analyze them entirely through natural language. You describe what you want — clean this, find the relationship between these columns, build a chart — and Julius writes, runs, and explains the Python code on your behalf. Every response shows the code it used, the output it produced, and a plain-English interpretation of the result.

- **Made by:** Julius AI
- **Type:** Conversational AI data analyst (chat-based, no-code)
- **Website:** [julius.ai](https://julius.ai)
- **Pricing:** Freemium — free tier available; paid plans for more messages and uploads

---

## Capabilities

- **Natural Language Data Analysis** — Ask questions about your data in plain English. Julius interprets the request, writes Python or R code, runs it, and explains the result — no coding required.
- **Automatic Data Profiling** — Upload any CSV and immediately get row/column counts, missing value summaries, data types, and descriptive statistics for all columns.
- **Data Cleaning via Prompts** — Instruct Julius to fix data quality issues — convert dtypes, parse mixed-format dates, handle nulls, drop irrelevant columns — with a single prompt.
- **Derived Column Creation** — Ask Julius to compute new fields like `tenure_years`, `age_check`, or `days_since_training` from existing columns; it handles the logic and appends them cleanly.
- **Statistical Analysis** — Run correlation analysis, group-level comparisons, segment breakdowns, and distribution summaries without writing a single line of code.
- **Chart Generation** — Prompt Julius to build bar charts, histograms, scatter plots, heatmaps, and more. It selects appropriate chart types based on the data and question.
- **Code Transparency** — Every analysis shows the exact Python code Julius executed, so you can learn from it, copy it, or verify it.
- **File Export** — Download cleaned datasets, dtype summaries, filtered subsets, and analysis outputs as CSV files directly from the chat.
- **Multi-turn Conversation** — Julius remembers the context of earlier prompts in the session. You can build iteratively — clean first, then analyze, then visualize — without repeating context.
- **Error Explanation** — If something unexpected appears in the data (e.g. a column that doesn't match expectations), Julius flags it and explains what it found.

---

## Use Cases

### 1. Instant Dataset Profiling
Upload any CSV and ask "Help me understand my data." Julius returns the row count, column count, missing value summary, numeric stats, and top categorical values — in seconds, with no setup.

### 2. Data Cleaning via Single Prompt
Describe the cleaning you need and Julius handles it end to end. It converts string columns to numeric, parses multi-format date columns, creates derived fields, and exports the cleaned file — all from one prompt.

### 3. Exploratory Statistical Analysis
Ask Julius to find relationships between columns, compare groups, or rank segments. It runs the analysis, explains what it found, and flags non-obvious patterns like weak or inverted correlations.

### 4. Chart Building Without Code
Prompt Julius to visualize any insight: "Show me attrition rate by department" or "Plot satisfaction vs engagement." It picks the right chart type and renders it immediately.

### 5. HR Workforce Analysis *(this repo's example)*
Used to analyze the **Messy HR Dataset** (2,845 rows, 28 columns) covering employee attributes, performance scores, training records, and engagement metrics. The workflow — done entirely through prompts — included:

| Prompt | What Julius did |
|---|---|
| *"Give me initial insights on this dataset"* | Profiled 2,845 rows × 28 cols; found 86.4% active employees; ranked departments by headcount (Production: 1,910); flagged attrition concentration in Production (16.9%) and Software Engineering (17.9%) |
| *"Clean my dataset, convert dtypes, parse all date columns, create derived columns"* | Parsed 4 mixed-format date columns (`StartDate`, `DOB`, `Survey Date`, `Training Date`); fixed dtypes across all 28 columns; created `tenure_years`, `age_check`, `days_since_training`; flagged mismatch between `Age` column and DOB-derived age |
| *"Find the relationship between EmployeeType, Performance, Satisfaction and EngagementScore"* | Ran correlation analysis (Satisfaction vs Engagement = -0.004, near zero); compared all three employee types × four performance levels; found PIP employees have consistently lower satisfaction; concluded performance is not a strong linear predictor of engagement |

> See [`examples/`](./examples/) for the raw dataset, cleaned dataset, dtype summary, and session export PDF.
> See [`screenshots/`](./screenshots/) for visuals from the Julius AI interface.

---

## Pricing

| Plan | Price | Key Details |
|---|---|---|
| Free | $0 | Limited messages per day, 1 file upload at a time |
| Pro | ~$25/month | Unlimited messages, multiple file uploads, priority access |
| Enterprise | Custom | Team features, API access, custom integrations |

---

## Links

- Website: [julius.ai](https://julius.ai)
- Documentation: [julius.ai/docs](https://julius.ai/docs)
- Blog: [julius.ai/blog](https://julius.ai/blog)
