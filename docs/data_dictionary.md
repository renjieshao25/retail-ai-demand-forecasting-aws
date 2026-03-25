# Data Dictionary

## Overview
This dataset is used for retail demand forecasting at the SKU-store-week level.

---

## Table: sales

| Column Name | Description | Data Type | Example | Used For |
|------------|------------|----------|--------|----------|
| id | Unique identifier for item-store combination | string | FOODS_1_001_CA_1_validation | Grouping |
| item_id | Product identifier | string | FOODS_1_001 | Forecasting |
| dept_id | Department identifier | string | FOODS_1 | Feature |
| cat_id | Category identifier | string | FOODS | Feature |
| store_id | Store identifier | string | CA_1 | Grouping |
| state_id | State identifier | string | CA | Feature |
| d_* | Daily unit sales (wide format; each column represents a day) | integer | d_1 = 3 | Target variable |
---

## Table: calendar

| Column Name | Description | Data Type | Example | Used For |
|------------|------------|----------|--------|----------|
| date | Actual calendar date | datetime | 2011-01-29 | Time series alignment |
| wm_yr_wk | Walmart retail week identifier (year + week) | integer | 11101 | Join with pricing data |
| weekday | Day name of the week | string | Saturday | Feature (seasonality) |
| wday | Numeric day of week (1=Saturday, 7=Friday) | integer | 1 | Feature (model input) |
| month | Month of year | integer | 1 | Feature (seasonality) |
| year | Year | integer | 2011 | Feature (trend) |
| d | Sequential day index used in sales data | string | d_1 | Join key with sales table |
| event_name_1 | Name of primary event/holiday | string | Christmas | Feature |
| event_type_1 | Type of primary event (e.g. Cultural, Sporting) | string | Cultural | Feature |
| event_name_2 | Name of secondary event/holiday | string | Easter | Feature |
| event_type_2 | Type of secondary event | string | Religious | Feature |
| snap_CA | SNAP active indicator for California (1 = active) | integer | 1 | Demand driver |
| snap_TX | SNAP active indicator for Texas (1 = active) | integer | 0 | Demand driver |
| snap_WI | SNAP active indicator for Wisconsin (1 = active) | integer | 1 | Demand driver ||

---

## Table: prices

| Column Name | Description | Data Type | Example | Used For |
|------------|------------|----------|--------|----------|
| store_id | Store identifier | string | CA_1 | Join key |
| item_id | Product identifier | string | FOODS_1_001 | Join key |
| wm_yr_wk | Walmart retail week identifier (year + week) | integer | 11101 | Join with pricing data |
| sell_price | Product price | float | 4.99 | Feature |
