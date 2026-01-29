# 📊 Power BI User Engagement & Churn Analytics

## 📌 Project Overview

This project is an end-to-end **data analytics case study** built using **Power BI Desktop (Free version)**. The goal is to analyze **user engagement, usage behavior, and churn** for a SaaS-style application using session-level and user-level data.

The project demonstrates:

* Proper data modeling (fact & dimension tables)
* Churn and retention analysis
* KPI design for product analytics
* Clean, interview-ready Power BI dashboards

---

## 📂 Dataset Description

The dataset is provided in an Excel file:

```
TrackDAU.xlsx
```

It contains **two sheets**:

---

## 🧩 Data Model

### 1️⃣ users_profiles (Dimension Table)

**Granularity:** 1 row per user

This table stores user-level attributes and churn indicators.

| Column               | Description                            |
| -------------------- | -------------------------------------- |
| user_id              | Unique user identifier (Primary Key)   |
| signup_date          | Date the user signed up                |
| country              | User country                           |
| plan                 | Subscription plan (Free / Paid / Tier) |
| signup_channel       | Acquisition channel                    |
| age_bucket           | User age group                         |
| total_sessions       | Total sessions by user                 |
| avg_session_length   | Average session duration               |
| avg_satisfaction     | Average satisfaction rating            |
| avg_tokens           | Average tokens used per session        |
| last_seen            | Last activity timestamp                |
| days_since_last_seen | Days since last activity               |
| churn_30d            | Churn flag (inactive for 30+ days)     |

---

### 2️⃣ sessions_enriched (Fact Table)

**Granularity:** 1 row per session

This table captures detailed session behavior and usage metrics.

| Column                      | Description                      |
| --------------------------- | -------------------------------- |
| session_id                  | Unique session identifier        |
| user_id                     | Associated user ID (Foreign Key) |
| session_number              | Session sequence for the user    |
| session_start / session_end | Session timestamps               |
| session_date                | Session date                     |
| session_length_minutes      | Session duration                 |
| device                      | Device type                      |
| usage_category              | Usage type                       |
| assistant_model             | Model used                       |
| prompt_length               | Prompt size                      |
| tokens_used                 | Tokens consumed                  |
| tokens_per_minute           | Usage intensity                  |
| satisfaction_rating         | Session satisfaction             |
| is_returning                | New vs returning session         |

> ⚠️ User attributes are duplicated in this table for analytical convenience, but **users_profiles** remains the source of truth for churn.

---

## 🔗 Relationships

* `users_profiles[user_id]` **1 → * `sessions_enriched[user_id]`
* Calendar table linked to `sessions_enriched[session_date]`

This follows a **star schema** best practice.

---

## 📉 Churn Definition

**Churn is defined as user inactivity.**

A user is marked as churned if:

> They have **no recorded sessions in the last 30 days**.

This is represented by the column:

```
churn_30d
```

* TRUE → churned user
* FALSE → active user

This is a **behavior-based (soft) churn** definition commonly used in SaaS analytics.

---

## 📐 Key KPIs

The following metrics are calculated using DAX in Power BI:

* Daily Active Users (DAU)
* Total Sessions
* Average Session Length
* Average Satisfaction Rating
* Churn Rate
* Returning vs New Sessions

---

## 📊 Dashboard Pages

### Page 1: Executive Overview

* DAU
* Total Sessions
* Avg Session Length
* Avg Satisfaction
* Churn Rate

### Page 2: Engagement Analysis

* Sessions over time
* DAU by country
* Session length by plan
* Tokens used trends

### Page 3: Retention & Churn

* Churn rate by plan
* Churn by signup channel
* Cohort-based churn analysis
* Days since last seen distribution

---

## 🛠️ Tools Used

* **Power BI Desktop (Free)**
* **Microsoft Excel** (data source)
* **DAX** for measures and KPIs

> Note: This project is fully executable using **Power BI Free** (no Pro license required).

---

## 🚀 How to Run the Project

1. Download and open **Power BI Desktop**
2. Load `TrackDAU.xlsx`
3. Import both sheets
4. Create relationships on `user_id`
5. Create a Calendar table
6. Build measures and dashboards

---

## 🎯 Skills Demonstrated

* Data modeling (fact & dimension tables)
* SaaS metrics & churn analysis
* Power BI dashboard design
* DAX fundamentals
* Analytical storytelling

---

## 📌 Use Cases

* Portfolio project for Data Analysts
* Power BI practice case study
* SaaS product analytics simulation
* Interview discussion material

---

## 📬 Next Improvements (Optional)

* Dynamic churn window (7/14/60 days)
* Retention curves & survival analysis
* LTV estimation
* Funnel analysis
* Predictive churn scoring

---

✅ **This project is designed to be clean, realistic, and portfolio-ready.**
