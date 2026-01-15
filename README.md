### Fiber Call Center Analytics 
This project highlights Business Intelligence solution to support Google Fiber Customer Service Team with a dashboard designed to gain insights into repeat callers.

**Business Problem:**
The team’s ultimate goal is to communicate with the customers to reduce the call volume and increase customer satisfaction and improve operational optimization. 

**Requirment Documents:**
After a collaborative project meeting, outlined are three key requirement documents that shaped the scope and direction of the solution.
 
**Data source:**
The project started with three cleaned datasets provided by the data engineer in .csv file. Although they came from different sources, the columns were standardized, making them ready for analysis.

1. market_1 - market_1.csv
2. Market_2 - market_2.csv
3. Market_3 - market_3.csv

**Data Processing:**
The datasets were loaded into BigQuery for analysis. As they shared the same column structure, I needed to write a query to union them into a single target table for further analysis and visualization.

```sql
SELECT 
date_created,
contacts_n,
contacts_n_1,
contacts_n_2,
contacts_n_3,
contacts_n_4,
contacts_n_5,
contacts_n_6,
contacts_n_7,
new_type,
new_market
FROM `tekstain-25.fibre.market_1`

UNION ALL

SELECT 
date_created,
contacts_n,
contacts_n_1,
contacts_n_2,
contacts_n_3,
contacts_n_4,
contacts_n_5,
contacts_n_6,
contacts_n_7,
new_type,
new_market
FROM `tekstain-25.fibre.market_2` 

UNION ALL

SELECT 
date_created,
contacts_n,
contacts_n_1,
contacts_n_2,
contacts_n_3,
contacts_n_4,
contacts_n_5,
contacts_n_6,
contacts_n_7,
new_type,
new_market
FROM `tekstain-25.fibre.market_3` 

```

**Query** 
![Query](images/Query.png)


**Query result** 
target table

![Query result](images/Query_result.png)

Results saved and downloded as .csv file, ready for further analysis and visualization in Tableau.


**Visualization**
- **Tool:** Tableua

![Day 0 Calls by Day of Week](images/Day_0_Calls_by_Day_of_Week.png)

**Key observations:**

- **Weekdays dominate call activity**, Monday through Friday account for the majority of calls each month.
- **Monday** consistently has the highest or near-highest share (18.4–18.6%) in January and February, suggesting a post-weekend surge in activity.
- In **March**, the pattern shifts slightly, **Wednesday and Thursday** see the highest call proportions (~18%), while Monday drops somewhat (15.4%).
- **Weekends (Saturday and Sunday)** show the lowest call volumes throughout, particularly Sunday (7–9%).
- The **distribution is relatively balanced across weekdays**, with small monthly variations but clear reduction on weekends.
**Overall insight:** Call activity is heavily concentrated during weekdays, especially early to mid-week, with a consistent decline on weekends — indicating business-hour or workweek-driven calling behavior.


![Market and Type for First Call](images/Market_and_Type_for_First_Call.png)

**Key observations:**

- **Market_1** has the highest overall call volume, dominated by **type_5 (1,806 contacts)** and **type_2 (1,180 contacts)** — indicating these two call types are major drivers in this market.
- **Market_2** has very low activity across all types, with **type_2** (105) and **type_5** (141) being the main contributors.
- **Market_3** shows moderate activity, again led by **type_5 (1,363 contacts)**, followed by **type_1 (267)** and **type_3 (176)**.
- **Type_4** is consistently minimal across all markets.
**Overall insight:**
Type_5 consistently generates the highest number of first repeat calls across all markets, especially in Markets 1 and 3. Market_2 has the lowest engagement overall, suggesting a need for further investigation into market conditions or operational factors there.

![Repeat Calls by Month](images/Repeat_Calls_by_month.png)

**Key observations:**

- **Overall repeat calls increased month over month**, rising from **21,134 in January** to **19,352 in February**, and peaking at **24,453 in March**, indicating growing repeat activity over time.
- Across all months, **“Contacts N”** consistently dominates, representing the largest share of total repeat calls by a wide margin.
- The remaining contact groups (**Contacts N1–N7**) show relatively stable but much smaller volumes, with slight growth from January to March.
- **March** shows the highest values across nearly all contact categories, reinforcing the upward trend in repeat calls.
**Overall insight:**
Repeat call volume is trending upward through the first quarter, with a particularly strong increase in March. The consistent dominance of “Contacts N” suggests it’s the key driver of overall repeat activity, potentially warranting deeper analysis into its causes and patterns.

![Repeat Calls by First Call](images/Repeat_Calls_by_First_Call.png)


![Calls by market and Type](images/Calls_by_Market_and_Type.png)


**Dashboard**


- **First Dashboard**

![Dashboard_1](images/Dashboard_1.png)


- **Second Dashboard**

![Dashboard_2](images/Dashboard_2.png)

- **Third Dashboard**

![Dashboard_3](images/Dashboard_3.png)
  
