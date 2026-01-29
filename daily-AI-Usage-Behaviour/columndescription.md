# Column Description

## 1. users_profiles (Dimension Table)

**Granularity:** 1 row per user

This table stores user-level attributes and churn indicators.

| Column | Description |
|--------|-------------|
| user_id | Unique user identifier (Primary Key) |
| signup_date | Date the user signed up |
| country | User country |
| plan | Subscription plan (Free / Paid / Tier) |
| signup_channel | Acquisition channel |
| age_bucket | User age group |
| total_sessions | Total sessions by user |
| avg_session_length | Average session duration |
| avg_satisfaction | Average satisfaction rating |
| avg_tokens | Average tokens used per session |
| last_seen | Last activity timestamp |
| days_since_last_seen | Days since last activity |
| churn_30d | Churn flag (inactive for 30+ days) |

## 2. sessions_enriched (Fact Table)

**Granularity:** 1 row per session

This table captures detailed session behavior and usage metrics.

| Column | Description |
|--------|-------------|
| session_id | Unique session identifier |
| user_id | Associated user ID (Foreign Key) |
| session_number | Session sequence for the user |
| session_start / session_end | Session timestamps |
| session_date | Session date |
| session_length_minutes | Session duration |
| device | Device type |
| usage_category | Usage type |
| assistant_model | Model used |
| prompt_length | Prompt size |
| tokens_used | Tokens consumed |
| tokens_per_minute | Usage intensity |
| satisfaction_rating | Session satisfaction |
| is_returning | New vs returning session |

> **Note:** User attributes are duplicated in this table for analytical convenience, but users_profiles remains the source of truth for churn.