# 🛒 Atliq Retail – Sales & Promotional Campaign Analysis

Welcome to a deep dive into Atliq Mart’s festive promotional strategy across southern India!

This **Power BI + SQL project** presents a comprehensive evaluation of two major campaigns — **Diwali 2023** and **Sankranti 2024** — run by Atliq Mart across 50+ retail outlets.  
The objective? To uncover what worked, what didn’t, and how future campaigns can be smarter, regionally optimized, and more profitable.

🔗 **Check out**: *https://www.linkedin.com/posts/abdulmalik2001_here-is-the-ppt-of-the-project-i-have-done-activity-7171556251812790272-MepS?utm_source=share&utm_medium=member_desktop&rcm=ACoAADKbN1QBdaahksntv2alURXh997AYubbSEk*

---

## 📊 Dataset Overview

**This project is powered by a structured dataset simulating real-world retail campaigns run by Atliq Mart. The data is spread across **4 CSV files**, including a central fact table and three supporting dimension tables.**

<img width="1193" height="756" alt="image" src="https://github.com/user-attachments/assets/8bd1a4f8-2c92-43ca-a565-6c34fd025762" />


### 🗃️ `dim_campaigns`  
Stores details of each promotional campaign.

| Column        | Description                                                            |
|---------------|------------------------------------------------------------------------|
| campaign_id   | Unique identifier for each promotional campaign.                       |
| campaign_name | Name of the campaign (e.g., Diwali, Sankranti).                        |
| start_date    | Start date of the campaign (DD-MM-YYYY).                               |
| end_date      | End date of the campaign (DD-MM-YYYY).                                 |

---

### 📦 `dim_products`  
Defines each product and its associated category.

| Column        | Description                                                                 |
|---------------|------------------------------------------------------------------------------|
| product_code  | Unique code assigned to each product.                                       |
| product_name  | Full product name including brand and specifications (e.g., size, weight).  |
| category      | Classification such as Grocery & Staples, Home Appliances, etc.            |

---

### 🏬 `dim_stores`  
Describes store locations and related metadata.

| Column   | Description                                                |
|----------|------------------------------------------------------------|
| store_id | Unique code identifying each store.                        |
| city     | The city where the store is located (geographic grouping). |

---

### 📈 `fact_events`  
Captures transactional-level promotional data across stores and products.

| Column                  | Description                                                                                  |
|-------------------------|----------------------------------------------------------------------------------------------|
| event_id                | Unique identifier for each sales event.                                                     |
| store_id                | Store where the event occurred (linked to `dim_stores`).                                     |
| campaign_id             | Campaign under which the event was recorded (linked to `dim_campaigns`).                    |
| product_code            | Product involved in the sales event (linked to `dim_products`).                             |
| base_price              | Standard price before any promotional discount.                                              |
| promo_type              | Type of promotion (e.g., 25% OFF, BOGOF, Cashback).                                          |
| quantity_sold_before_promo | Units sold the week before the campaign (used as baseline).                            |
| quantity_sold_after_promo  | Units sold during the campaign period.   
