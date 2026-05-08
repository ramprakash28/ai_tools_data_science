# Deepnote

## Overview

**Deepnote** is a cloud-based, collaborative data science notebook platform built for teams. It brings together the familiarity of Jupyter notebooks with real-time collaboration, built-in AI assistance, SQL support, and publishing capabilities — all in the browser without any local setup.

- **Made by:** Deepnote Inc.
- **Type:** Cloud-based collaborative notebook
- **Website:** [deepnote.com](https://deepnote.com)
- **Pricing:** Freemium — free tier available; paid plans for teams

---

## Capabilities

- **Real-time Collaboration** — Multiple users can work in the same notebook simultaneously, similar to Google Docs. See live cursors, edits, and outputs from teammates.
- **AI Assistant (Deepnote AI)** — Built-in AI that can generate code, explain outputs, suggest fixes, and answer questions about your data directly inside the notebook.
- **SQL Support** — Write and run SQL queries natively inside notebooks alongside Python code. Connect to databases without leaving the environment.
- **Data Source Integrations** — Connect to PostgreSQL, MySQL, BigQuery, Snowflake, Redshift, S3, Google Sheets, and more with a few clicks.
- **Scheduled Runs** — Automate notebook execution on a schedule (hourly, daily, weekly) without external orchestration tools.
- **Dashboards & Publishing** — Convert notebooks into shareable dashboards or reports. Publish with a link — no coding required for viewers.
- **Environment Management** — Pin Python/R versions, manage packages via `requirements.txt`, and use persistent environments across sessions.
- **Version History** — Track changes to notebooks over time and restore previous versions.
- **Variable Explorer** — Inspect dataframes, variables, and outputs interactively in a sidebar without writing extra print statements.
- **Terminal Access** — Run shell commands directly within the platform.
- **Commenting** — Leave inline comments on specific cells for code review or team discussions.

---

## Use Cases

### 1. Exploratory Data Analysis (EDA)
Load a dataset, profile it, visualize distributions, and share the notebook with teammates — all without any local installation. Deepnote's variable explorer and inline outputs make the iteration cycle fast.

### 2. Collaborative Research Projects
Multiple data scientists can work on the same notebook at the same time. Useful for pairing on feature engineering, reviewing model outputs, or running experiments together.

### 3. Automated Reporting
Schedule notebooks to run daily and publish the output as a dashboard. Useful for recurring business reports, KPI monitoring, or weekly summaries sent to stakeholders.

### 4. SQL + Python Workflows
Query a database with SQL, pull results directly into a Python dataframe, and continue analysis in the same notebook — no context switching between tools.

### 5. Teaching and Demos
Share a live notebook link with students or stakeholders. Viewers can see outputs without needing a Python environment. Instructors can comment inline on student notebooks.

### 6. Mental Health & Social Media Analysis *(this repo's example)*
Used to analyze the **Teen Mental Health Dataset** (1,200 records) from Kaggle. The project explored how daily social media usage, sleep patterns, screen time before bed, and platform choice relate to depression, anxiety, stress, and addiction levels in teenagers aged 14–19. A dashboard was built in Deepnote summarizing key findings across gender, platform, and age groups.

> See [`examples/`](./examples/) for the dataset and exported dashboard used in this project.

---

## Pricing

| Plan | Price | Key Limits |
|---|---|---|
| Free | $0 | 5 projects, 5GB storage, community support |
| Team | From $12/user/month | Unlimited projects, scheduled runs, SSO |
| Enterprise | Custom | Custom compute, advanced security |

---

## Links

- Website: [deepnote.com](https://deepnote.com)
- Documentation: [docs.deepnote.com](https://docs.deepnote.com)
- Integrations: [deepnote.com/integrations](https://deepnote.com/integrations)
- Blog: [deepnote.com/blog](https://deepnote.com/blog)
