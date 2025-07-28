# 📊 Power BI Sales Dashboard – Global Superstore

An interactive Power BI dashboard built using the Global Superstore dataset to analyze sales performance, profitability, return trends, and customer segments across different regions and years.

---

## 🗂️ Dataset

- **Source:** Global Superstore 2016 (`global_superstore_2016.xlsx`)
- **Records:** Orders, Returns, Customers, Regions
- **Time Span:** 2012 to 2015
- **Key Columns:** Sales, Profit, Quantity, Category, Sub-Category, Customer Name, Order Date, Region, Market, Segment

---

## 🧹 Data Cleaning and Preparation

Performed using **Power Query Editor**:
- Removed null or blank records
- Formatted date columns (`Order Date`, `Ship Date`)
- Joined **Returns** table with **Orders** using `Order ID` to calculate return metrics
- Extracted **Year** from `Order Date` for time-series analysis
- Cleaned `Profit` column to fix negative/positive inconsistencies (if any)

---

## 🧠 Key DAX Measures

```DAX
Total Sales = SUM(Orders[Sales])

Total Profit = SUM(Orders[Profit])

Total Quantity = SUM(Orders[Quantity])

Return Orders = CALCULATE(COUNTROWS(Returns), RELATEDTABLE(Orders))

Average Delivery Days = AVERAGE(Orders[Delivery Days])

Top Customers = 
TOPN(10, 
    SUMMARIZE(Orders, Orders[Customer Name], "TotalProfit", SUM(Orders[Profit])),
    [TotalProfit], DESC
)
📈 Dashboard Features
✅ KPI Cards:
Total Sales: $12.64M

Total Quantity: 178.3K units

Average Delivery Days: 4 days

Return Orders: 1,079

✅ Visuals:
Top Profitable Products: Canon ImageClass, Cisco Smart Switches, etc.

Top Loss-Making Products: Bevis Comm Devices, Cubify Cube 3D printers, etc.

Sales by Segment: Consumer (51.5%), Corporate, Home Office

Sales by Region: Asia Pacific, USCA, Europe, etc.

Top Profitable Customers: Tamara Chand, Raymond Buch, Sanjit Chand

Profit Trends: Year-wise and Market-wise

🔍 Insights Derived
📉 Certain products like Bevis Routers and Cubify Printers consistently resulted in losses.

📈 Majority of profits came from the Consumer segment and Asia Pacific region.

🚚 Average delivery time remained steady at around 4 days, showing consistent logistics.

💸 A few customers (e.g., Tamara Chand) significantly contributed to overall profitability.

📦 Over 1,000 return orders were identified, making returns a key area for improvement.

🧰 Tools Used
Power BI Desktop

Power Query

DAX

Excel (.xlsx)

