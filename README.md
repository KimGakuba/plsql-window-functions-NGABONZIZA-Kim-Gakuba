# **👤 Student Profile**  

🔹 **NAME:** NGABONZIZA Kim Gakuba  
🔹 **ID:** `27670`  
🔹 **GROUP:**  **D**  

---
# FMCG Sales and Inventory Analysis Project 📊

## Business Context ?
A Rwandan and regional neighboring region medium-sized regional wholesale distributor imports and distributes Fast-Moving Consumer Goods (FMCG) items such as snacks, beverages, cooking oil, and toilet products. SKU-level visibility is required by Sales and Supply Chain organizations by geography to prevent stockout and overstock, enabling inventory management to be optimal and efficient distribution.

---
## Data Challenge ?
The sales and inventory data present are siloed:
- Point of Sale (POS) daily feeds and weekly reports contain sales data.
- Product codes vary in datasets.
- Individual discounts and returns are captured in Excel sheets.

This fragmentation prevents SKU-level, geographic, and time-series analysis, leading to stockouts of best SKUs in some districts and others in warehouses.

---
## Expected Outcome ??? 
The project will enable actionable insight through:
- **SKUs by Region and Quarter**: Track top SKUs by region and quarter.
- **Total Month Sales**: Add monthly sales of every SKU.
- **Month-over-Month Growth**: Determine growth patterns to reflect changes in demand.
- **Customer Spend Quartiles**: Segment customers into spend quartiles to enable targeted promotions.
- **3-Month Moving Averages**: Level out volatility to enable replenishment and redistribution efforts.

## Key Success Metrics ?

1. **Top 5 SKUs by Region/Quarter**: Get top 5 SKUs by volume by quarter by region with `RANK()` skewed towards heavy-demanding SKUs.
2. **Rolling Monthly Sales Totals**: Get rolling sales totals by month by SKU with `SUM() OVER()` to see sales performance over time.
3. **Month-over-Month Growth**: Get percentage sales growth by SKU compared to last month using `LAG()` or `LEAD()` to identify demand trends.
4. **Customer Quartiles**: Segment customers into four equally sized spend quartiles by using `NTILE(4)` so promotions can be directed accordingly.
5. **3-Month Moving Averages**: Make 3-month rolling averages of sales per SKU by using `AVG() OVER()` so the fluctuation of demand can be smoothed out to be predicted.

## Database Schema 💻

### 1. MySQL codes for creating Customer, products,transactions Tables
#### 1. creating Customer
![Creating Customer Table](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20customers.png)
#### 2. Creating products
![Creating products Table](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20products.png)
#### 3. Creating transactions
![Creating transactions Table](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20transactions.png)
#### 4. Creating returns_discounts
![Creating returns_discounts Table](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20returns_discounts.png)
*Caption: Screenshot of creating the `customers` table with columns for customer ID, name, and region.*

### 2. Inserting Sample Data
#### 1. inserting into customers 
![Inserting Data into customers](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/insert%20codes%20in%20costomers.png)

---
#### output
![Sample Data](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/values%20of%20customers.png)

---
#### 2. inserting into products 
![Inserting Data into products](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/insert%20codes%20into%20products.png)

---
#### output
![Sample Data](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/values%20of%20products.png)

---
#### 3. inserting into transactions 
![Inserting Data transactions](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/insert%20codes%20into%20transcations.png)

---
#### output
![Sample Data](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/values%20of%20transactions.png)
*Caption: Screenshot of inserting sample data into `customers`, `products`, and `transactions` tables.*

---
### 3. Table Creation 
![Table Creation Scripts](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/show%20tables.png)
*Caption: Screenshot of SQL showing tables created `customers`, `products`, `transactions`, and `returns_discounts` tables.*

### 4.  Also Included an ER diagram: which consists of the following;
Entity 'Customers' (rectangle): attributes in ovals - customer_id (PK), name, region.
Entity 'Products' (rectangle): attributes in ovals - product_id (PK), sku (unique), name, category.
Entity 'Transactions' (rectangle): attributes in ovals - transaction_id (PK), customer_id (FK), product_id (FK), sale_date, quantity, unit_price, amount (computed), region.
Entity 'Returns_Discounts' (rectangle): attributes in ovals - rd_id (PK), transaction_id (FK), rd_date, rd_amount, reason.
![ER Diagram](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/ERDIAGRAM.png)

## Implementation of SQL Window Functions 🛠️

### 1. Ranking: ROW_NUMBER(), RANK(), DENSE_RANK(), PERCENT_RANK() 📊
These functions assign ranks or row numbers to rows based on ordering, useful for identifying top performers like top N customers by revenue, handling ties differently.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20ranking%20.png)

---

![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/output%20of%20ranking.png)

### 2. Aggregate: SUM(), AVG(), MIN(), MAX() with frame comparisons (ROWS vs RANGE) 📈
Aggregate functions compute cumulative or windowed values like sums or averages over partitions, with ROWS for physical rows and RANGE for logical value ranges, ideal for running totals and trends.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20aggregate.png)

---

![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/output%20of%20aggregate.png)

### 3. Navigation: LAG(), LEAD(), growth % calculations 🔄
Navigation functions access data from previous (LAG) or next (LEAD) rows in a partition, enabling calculations like month-over-month growth for period-to-period analysis.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20navigation.png)

---

![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/output%20of%20navigation.png)

### 4. Distribution: NTILE(4), CUME_DIST() 📉
Distribution functions divide rows into buckets (NTILE) or compute cumulative distribution (CUME_DIST), perfect for segmenting data like customers into quartiles based on spending.
![Code Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/codes%20of%20distribution.png)

---

![Table Screenshot](https://github.com/KimGakuba/plsql-window-functions-NGABONZIZA-Kim-Gakuba/blob/main/all_screenshots/output%20of%20ditribution.png)

## Results Analysis 📊
---
### 1. **Descriptive – What Happened? (Patterns, Trends, Outliers)**
Patterns of Sales: Top SKU in sales was Organic Salted Chips 50g with a sale of 40 units and 1,200 revenue, well ahead of Coffee Beans 250g (20 units, 500 revenue) and Cooking Oil 2L (6 units, 72 revenue). This positions snacks as the top FMCG demand within the data set.
Regional Trends: Ruhengeri experienced the sharpest increase, with revenues increasing from 0 in early 2024 to 800 in total (peaking at 600 in April). Kigali was highest in volume (450 in total) but dipped from 250 in January to 50 in March. Butare was low-volume (522 in total) but consistent.
Customer Spending: The highest spending customer was Amina Uwizeyimana of Ruhengeri with 800, followed by Paul Kagabo of Butare at 522 and John Doe of Kigali at 450. Something peculiar: March sales in Kigali declined 79% from February, perhaps a regional downturn.
Inventory Trends: Inventories at the moment are healthy as a norm (Coffee: 80 units, Chips: 60, Oil: 94), with Chips drying out most rapidly at 40% of original stock and Oil at 94% capacity.

---
### 2. **Diagnostic – Why? (Causes, Comparisons, Influencing Factors)**
Product Demand Drivers: Chips snack form would seem to be driven by impulse buys and high unit price (30 compared to 12 for Oil), generating 62% of total revenue while being equal in initial inventory. Coffee drinks have steady but low demand, maybe seasonal, and Oil lags because it is volume-driven (sold only 6 units), illustrating it is a normal with sporadic bulk buying.
Regional Differences: Ruhengeri's 300% April rise (compared with Kigali's decline) could be attributable to local promotion or increases in rural economics, compared with possible saturation or competition in urban Kigali. Stability in Butare indicates consistent low-end demand but low market penetration.
Customer Factors: Maximum spenders (Amina and Paul) are matched by high-density locations (Ruhengeri/Butare), with product range propelling them—highest was Amina's 20 units purchase of Chips. Kigali's outlier drop can be explained by reduced spending (only 3 against Ruhengeri's 2 spend-maxing ones), perhaps as a result of supply or external conditions.
Inventory Drivers: Sudden drawdown in Chips (versus excess Oil) indicates out-of-balances levels of replenishments; rate of sales (40 units/4 months) overwhelms Oil's (1.5/month), putting stockouts in the horizon if not halted.

---
### 3. **Prescriptive – What Next? (Recommendations, Business Actions)**
Inventory Replenishment: Advance Chips to 80+ units immediately (target 20% buffer above rate of sales); redistribute 20 units of Oil from Butare/Kigali warehouses to Ruhengeri to level loads and prevent ageing stock.
Promotions & Redistribution: Invent promotion snacks opportunities in Kigali (e.g., bundle Chips with Coffee at 10% discount) to reverse the 79% dip; redirect excess Oil stocks through cross-regional discounting to Butare, expecting 15% sales increase in staples.
Customer Strategies: Segment high spenders like Amina into a loyalty program (e.g., 5% repeat-purchase discount) to maintain them; investigate Kigali's downturn through POS audits and re-target John Doe with targeted promotions to recover 20% lost volume.
Monitoring Actions: Develop bi-monthly SKU-by-SKU dashboards showing MoM growth and 3-month averages; cause alarms for >30% regional volatility to enable anticipatory redistribution, targeting 10-15% stockout/excess reduction.

---

## References
1. MySQL 8.0 Reference Manual — Window Functions
2. Oracle Documentation: RANK, NTILE.
3. Mode Analytics — SQL Window Functions Tutorial
4. Youtube videos - helping me to turke the challengee 
5. SQL Window Functions in Practice — Blog series
6. Git Bash- git terminal
7. Gartner — Inventory Optimization Primer
8. Moving Averages and Reorder Points — Supply Chain texts
9. Edrawmax- for drawing the ER Diagram
10. Academic papers on demand forecasting and inventory management

### “All sources were properly cited. Implementations and analysis represent original work. No AIgenerated content was copied without attribution or adaptation.”


# “Whoever is faithful in very little is also faithful in much.” – Luke 16:10
