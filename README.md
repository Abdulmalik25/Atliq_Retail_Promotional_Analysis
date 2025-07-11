# 🛒 Atliq Retail – Sales & Promotional Campaign Analysis

Welcome to a deep dive into Atliq Mart’s festive promotional strategy across southern India!

This **Power BI + SQL project** presents a comprehensive evaluation of two major campaigns — **Diwali 2023** and **Sankranti 2024** — run by Atliq Mart across 50+ retail outlets.  
The objective? To uncover what worked, what didn’t, and how future campaigns can be smarter, regionally optimized, and more profitable.

🔗 **Click -> to view the project post on LinkedIn**: [View Link](https://www.linkedin.com/posts/abdulmalik2001_here-is-the-ppt-of-the-project-i-have-done-activity-7171556251812790272-MepS?utm_source=share&utm_medium=member_desktop&rcm=ACoAADKbN1QBdaahksntv2alURXh997AYubbSEk)


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
| quantity_sold_after_promo  | Units sold during the campaign period.                                                 |



## 🔍 Key Analyses & Dashboards

### 🏪 1. Store Performance Analysis

**Goal:** Evaluate which stores and cities contributed most to revenue and sales uplift during campaigns.

<img width="1276" height="724" alt="image" src="https://github.com/user-attachments/assets/38f293cc-0071-4dec-8fb9-982263f3ff30" />

**Key Findings:**
- **Top performing cities**: Mysuru, Chennai, and Bengaluru generated the highest Incremental Revenue (IR).
- **Highest-performing store**: `STMYS-1` in Mysuru topped all stores with ₹6.4M IR.
- **Underperforming cities**: Mangalore, Trivandrum, and Visakhapatnam had the lowest IR.
- Cities with **more store density performed better**, suggesting the importance of regional presence.
- **City-wise IR and ISU were aligned**, indicating consistent promotion effectiveness in top-performing regions.

---

### 🧾 2. Promotion Type Analysis

**Goal:** Understand which types of promotions were most effective in driving sales and revenue.

<img width="1278" height="717" alt="image" src="https://github.com/user-attachments/assets/79b45a61-ec02-4aa5-b3b3-2ae525b758f2" />

**Key Findings:**
- **Best performing promotions**:
  - `500 Cashback`: Delivered ~59% IR, making it the most effective promotion.
  - `BOGOF (Buy One Get One Free)`: Contributed ~33% IR and strong unit sales uplift.
- **Worst performing promotion**:
  - `25% OFF`: Recorded negative IR and ISU, indicating poor performance.
- **33% and 50% OFF** promotions provided marginal gains.
- **Seasonally-aligned promotions** (e.g., BOGOF for Sankranti groceries) delivered better results.

---

### 📦 3. Category & Product Analysis

**Goal:** Identify which product categories and individual items performed best or worst during the campaigns.

<img width="1280" height="722" alt="image" src="https://github.com/user-attachments/assets/b2b36979-f68f-4789-be83-aa1b5762ad09" />

**Key Findings:**
- **Top categories by ISU**:
  - `Home Appliances`: Highest sales uplift during Diwali.
  - `Combo Products`: Strong performers in cashback campaigns.
- **Top products by IR%**:
  - `Waterproof Immersion Rod`, `LED Bulbs`, `Bedsheet Set`, and `Curtains` under BOGOF.
  - `Home Essentials Combo` under 500 Cashback also performed exceptionally.
- **Poor-performing products**:
  - Items under 25% OFF — especially `Scrub Sponge`, `Fusion Container Set`, and low-cost lotions/soaps — showed negative IR%.
- **Strategic timing**:
  - High-value items like appliances thrived during Diwali.
  - Grocery and daily-use items responded better to promotions during Sankranti.

---

## 🧠 Ad-Hoc SQL Insights

Five real-world business questions answered using SQL queries:

### 🧾 Request 1:  
**Products with base price > ₹500 under 'BOGOF'** 
<img width="1276" height="718" alt="image" src="https://github.com/user-attachments/assets/5e92e02d-e448-4efa-b6e3-9c8106963da0" />


### 🧾 Request 2:  
**Store count by city**  
<img width="1272" height="692" alt="image" src="https://github.com/user-attachments/assets/abbb81da-cded-4799-b0d3-49cb4530eaf4" />


### 🧾 Request 3:  
**Revenue before & after promotions**  
<p>
  <img src="https://github.com/user-attachments/assets/a7899709-3055-4894-b1df-54286dcd1c42" width="49%" />
  <img src="https://github.com/user-attachments/assets/44da7064-9310-4fa6-ad21-03927de4472e" width="49%" />
</p>


### 🧾 Request 4:  
**ISU% by category during Diwali**  
<img width="1287" height="724" alt="image" src="https://github.com/user-attachments/assets/9ac180f8-1b61-4667-aeff-1da18235323d" />
<img width="1286" height="716" alt="image" src="https://github.com/user-attachments/assets/d660e6da-9fc1-475a-9750-4baec8629f4a" />


### 🧾 Request 5:  
**Top 5 products by IR%**  
<p>
  <img src="https://github.com/user-attachments/assets/d660e6da-9fc1-475a-9750-4baec8629f4a" width="49%" />
  <img src="https://github.com/user-attachments/assets/fda702d4-5ca6-4351-9e0b-e7faaa7eb1a3" width="49%" />
</p>


---
## 💡 Recommendations

### 🎯 1. Prioritize High-Performing Cities
- Expand presence in **Mysuru, Chennai, and Bengaluru** — cities that generated the highest Incremental Revenue (IR).
- Reevaluate strategy and campaign execution in **Mangalore, Trivandrum, and Visakhapatnam**, which consistently underperformed.

---

### 🧾 2. Refine Promotion Strategy
- Scale up **500 Cashback** and **BOGOF** promotions — proven to deliver strong IR and unit sales uplift.
- Discontinue or redesign **25% OFF** offers due to their negative impact on revenue and sales.
- Align promotion types with seasonal behavior:  
  - Use **BOGOF** during Sankranti for groceries  
  - Use **Cashback** during Diwali for electronics and high-value items

---

### 📦 3. Focus on High-Value Product Bundles
- Prioritize promotion of **combo packs** and **appliance bundles**, especially during festive seasons.
- Highlight high-IR items such as **Bedsheet Set**, **LED Bulb**, and **Home Essentials Combo**.

---

### 🏙️ 4. Optimize Store Network by Region
- Invest in cities with strong store density and campaign response (e.g., Bengaluru, Chennai, Hyderabad).
- Use store count and revenue correlation data to guide **future store expansion and resource allocation**.

---

### 🧠 5. Personalization & Loyalty Programs
- Launch **loyalty rewards** for repeat buyers in top-performing product categories.
- Implement **region-based personalized offers** using segmentation from campaign performance data.

---

### 🔁 6. Seasonal Timing Optimization
- Run high-value product campaigns during **Diwali**, which has shown stronger sales impact.
- Use **combo offers and daily-use essentials** during **Sankranti**, when value-focused shopping behavior is high.


## 🎯 Conclusion

This campaign analysis reveals a surprising truth: **not all discounts drive value** — and sometimes, **less flashy strategies like Cashback outperform heavy markdowns** like 25% OFF. By digging into store-level performance, category alignment, and promo timing, Atliq Mart can now make **data-backed decisions** instead of running on retail intuition.

What stands out is the **power of regional behavior**. Cities like Mysuru, Chennai, and Bengaluru weren't just high-volume — they were strategically positioned for success, aided by store density and promotion fit. Meanwhile, lower-tier cities struggled, showing that **"one-size-fits-all" marketing no longer works** in India’s diverse retail landscape.

Perhaps most surprisingly, high-ticket items like **bedsheets, immersion rods, and appliance combos** emerged as the unexpected champions under BOGOF and Cashback schemes — proving that customers are willing to spend more when value is structured right.

This project isn’t just a festive sales post-mortem — it’s a **framework for smarter seasonal planning, regional targeting, and product bundling**. With the right mix of **data storytelling and strategic action**, Atliq Mart is well-positioned to turn future promotions into powerful revenue engines.




















































