## Problem Statement

India’s largest intra-city logistics marketplace, aims to revolutionize delivery services by leveraging technology to provide accurate delivery time estimates, a key driver of customer satisfaction. This project focuses on predicting delivery times using a dataset of order and delivery details, including market areas, restaurant categories, order volumes, and partner availability.

1. To develop a predictive model that delivers ***precise delivery time estimates, reducing customer churn and improving satisfaction***
2. To optimize the ***allocation of delivery partners*** by understanding demand patterns and operational capacity
3. To identify bottlenecks causing delays, enabling ***operational efficiency gains***

By employing exploratory data analysis, feature engineering, and machine learning models ***(Random Forest, XGBoost, and Neural Networks)***, this analysis seeks to provide actionable insights that enhance company's ability to ensure timely deliveries and streamline logistics operations

**Data**

<img src="Pictures/features.png" alt="Data" width="500"/> 

This dataset is about each order placed from different restaurants located in different areas and our goal is to predict delivery time of these orders. Data has 1,97,428 rows where each row represents an order

**Assumptions:**

* Since the number of on-shift partners is less than the number of busy partners, I assume that on-shift partners represent the available delivery partners at the time of the order, while busy partners refer to those who are currently offline
* The metrics for delivery partners and outstanding orders are indicative at the platform level rather than being specific to individual markets

## EDA

***Uni-variate Analysis***

<img src="Pictures/percentage_share.png" alt="Data" width="800"/> 

***Market Area Distribution***

The majority of restaurants (around 70%) are located in market areas 1.0, 2.0, and 4.0.
The distribution is visualized using a pie chart, where different shades of blue represent different market areas.

***Mode of Payment Distribution***

About 75% of orders are paid through modes 1.0, 3.0, and 5.0.
Modes 6.0 and 7.0 have a negligible share of payments.
The pie chart highlights this distribution with pastel colors, and less frequent payment modes are slightly separated (exploded) for better visibility.
These insights help in understanding restaurant distribution and customer payment preferences, which can be valuable for strategic decision-making

***Restaurant categories***

<img src="Pictures/Top_restaurant_categories.png" alt="Data" width="800"/> 

* Above chart shows what type of restaurants people mostly order from
* American, Pizza & mexican are the most popular type of restaurants

<img src="Pictures/items_and_subtotal.png" alt="Data" width="800"/> 

* Most of the orders have total no. of items <= 5
* Most of the orders have sub total between < 5000
* Distribution is slightly skewed towards right, maybe because of large corporate or party orders

<img src="Pictures/min_and_max.png" alt="Data" width="800"/> 

* Average min value of item < 1000 whereas average max value per item > 1000
* Values range between 0 & 14,000, maybe there could be some outliers since some values are very high and isolated

<img src="Pictures/onshift_and_busy_partners.png" alt="Data" width="800"/> 

* Median value at the time of order: on-shift delivery partners - 37, busy delivery partners - 34

<img src="Pictures/total_outstanding_orders.png" alt="Data" width="800"/> 

* Average total outstanding orders = 58

***Extracting Time & Day of the week***

<img src="Pictures/extracting_time_and_day.png" alt="Data" width="800"/>
<img src="Pictures/time_day_delivery.png" alt="Data" width="800"/> 

* Peak time is from 1am to 3 am & 7pm to 9 pm
* No. of orders at 2am is double of no. of orders at 8pm
* Average delivery time is around 48 mins whereas median delivery time is 44 mins
* Max delivery time is around 1,41,948 mins which is clearly an outlier
* No. of orders are higher during weekends i.e. saturday & sunday compared to weekdays

***Bi-variate Analysis***

<img src="Pictures/bivariate1.png" alt="Data" width="800"/>

* Average delivery time is increasing with increase in total outstanding orders
* Average delivery time remains constant till total outstanding orders reach 50 and then increase linearly with total outstanding orders
* As total outstanding orders cross 200, delivery time is increasing non-linearly
* Average delivery time increases linearly with max item price & sub - total

<img src="Pictures/bivariate2.png" alt="Data" width="800"/>

* Average delivery time is fluctuating as total no. of items are increasing
* Initially, as no. of total on-shift/busy delivery partners increases till 30, average delivery time decreases
* As no. of on-shift/busy delivery partners crosses 30, average delivery time increases

<img src="Pictures/bivariate3.png" alt="Data" width="800"/> 

* Average delivery time increases linearly as no. of disntict items increases
* Average delivery for market id 1 is around 54 mins whereas for rest of the market ids, average delivery time is around 46 mins
* Avg delivery time is highest during: sunday > monday > saturday > thursday > tuesday > friday > wednesday

<img src="Pictures/bivariate4.png" alt="Data" width="800"/>

* Average delivery time decreases from 52 to 41 as we move from 1 to 7, but only for 6, it increases to 60
* Unusual spike in average delivery time at 8am

## Data Pre-Processing

* 16,262 rows have missing values in on-shift partners, busy partners & outstanding orders together, which forms 8% of total data
* Significant correlation for on-shift partners, busy partners & outstanding orders is with each other and with:
* hour of the day

Assumptions:        

Since values have variance at each hour, assuming they follow normal distribution, imputation will be done using mean & std for individual feature
