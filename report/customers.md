# Olist Customers Dataset Documentation

## Overview
This dataset contains information about the customers who made purchases on the Olist e-commerce platform. It includes location data and identifiers used to track both individual orders and repeat buyers.

## Dataset Summary
Source: Kaggle Olist Dataset(https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce?utm_source=chatgpt.com)

Original File: olist_customers_dataset.csv
Rows: 99,441

Columns: 5

Primary Key: customer_id
## Files
During the cleaning process, this dataset was split into two separate files depending on the analytical use case:
1. `cleaned_customers_all.csv` (99,441 rows): Contains all customer records tied to every single order. **Use this for joining with the Orders table or calculating revenue.**
2. `cleaned_customers.csv` (96,096 rows): Deduplicated dataset containing only one record per actual human being. **Use this for demographic analysis or counting total users.**

---

## Data Dictionary

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `customer_id` | String | A unique token generated for every single *order*. If a user makes 3 purchases, they will have 3 different `customer_id`s. Use this as the Primary Key to join with the `orders` dataset. |
| `customer_unique_id` | String | The unique identifier for the actual human being. Use this column to identify repeat buyers or count the total user base. |
| `customer_zip_code_prefix` | String | The first 5 digits of the customer's zip code. |
| `customer_city` | String | The city where the customer is located. |
| `customer_state` | String | The 2-letter state abbreviation where the customer is located (e.g., 'SP' for São Paulo). |

---

## Data Cleaning & Transformations Applied
The following steps were taken to clean the raw data before analysis:
* **Zip Code Formatting:** Zip codes were converted to `String` and padded with leading zeros (`.zfill(5)`) to fix Pandas automatically dropping them from zip codes starting with `0`.
* **City Name Standardization:** All city names were converted to lowercase and special Portuguese accent marks (like `ã` or `é`) were stripped to prevent duplicate city groupings.

## Data Quality
- No missing values found.
- No duplicate rows found.
- Data types verified.
- ZIP codes reformatted to preserve leading zeros.