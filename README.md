## Problem Statement

Porter, India's largest marketplace for intra-city logistics, is revolutionizing the delivery sector with technology-driven solutions. Analyzing this dataset can provide significant insights into delivery dynamics, efficiency bottlenecks, and optimization opportunities. The insights obtained can enhance Porter's operational efficiency, ensuring timely deliveries and improving driver-partner allocation.

***Data***

<img src="Pictures/features.png" alt="Data" width="500"/> 

This dataset is about each order placed from different restaurants located in different areas and our goal is to predict delivery time of these orders. Data has 1,97,428 rows where each row represents an order.

***Problem Statement - Decoded***

1. Providing precise delivery estimates - Improves customer satisfaction and reduces churn
2. Proper allocation of delivery partners - Optimised operational costs
3. Identifying bottlenecks - Reducing higher delivery times

## EDA

***Uni-variate Analysis***

<img src="Pictures/percentage_share.png" alt="Data" width="800"/> 

* Around 50% of the restaurants are located in area: 2.0 or 4.0
* Around 75% of the orders are paid through modes: 1.0, 3.0, 5.0 whereas 6.0 & 7.0 are almost negligible

***Restaurant categories***

<img src="Pictures/Top_restaurant_categories.png" alt="Data" width="800"/> 

* Above chart shows what type of restaurants people mostly order from
* American, Pizza & mexican are the most popular type of restaurants

<img src="Pictures/percentage_share.png" alt="Data" width="800"/> 
<img src="Pictures/percentage_share.png" alt="Data" width="800"/> 
<img src="Pictures/percentage_share.png" alt="Data" width="800"/> 
<img src="Pictures/percentage_share.png" alt="Data" width="800"/> 

* Most of the orders have total no. of items <= 5
* Most of the orders have sub total between < 5000
* Distribution is slightly skewed towards right, maybe because of large corporate or party orders

* Average min value of item < 1000 whereas average max value per item > 1000
* Values range between 0 & 14,000, maybe there could be some outliers since some values are very high and isolated
