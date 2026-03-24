# Data Dictionary

## Overview
This dataset is used for retail demand forecasting at the SKU-store-week level.

---

## Table: sales

| Column Name | Description | Data Type | Example | Used For |
|------------|------------|----------|--------|----------|
| date | Transaction date | datetime | 2020-01-01 | Time series |
| store_id | Unique store identifier | string | CA_1 | Grouping |
| sku_id | Unique product identifier | string | FOODS_1_001 | Forecasting |
| units_sold | Number of units sold | integer | 12 | Target variable |
| price | Selling price per unit | float | 4.99 | Feature |
| promo_flag | Whether item is on promotion | boolean | 1 | Feature |
| inventory_on_hand | Units available in stock | integer | 100 | Feature |
| category | Product category | string | FOODS | Feature |

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
| sku_id | Product identifier | string | FOODS_1_001 | Join key |
| week | Week identifier | string | 2020-W01 | Join key |
| price | Product price | float | 4.99 | Feature |
