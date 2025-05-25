 # RFM Analysis 

## 1. Introduction and Goal 
### Introduction 
In today's competitive marketplace, businesses strive to understand customer behavior in order to increase engagement, retention, and sales. One of the most effective methods for this is the RFM (Recency, Frequency, Monetary) analysis, a proven framework that segments customers based on how recently they have made a purchase (Recency), how often they purchase (Frequency), and how much they spend (Monetary). By leveraging RFM analysis, companies can better target their customers, optimize marketing efforts, and boost revenue. In this project, we utilize the RFM framework to segment customers from a dataset that includes orders, customer information, products, and locations, to draw actionable insights for the business.

### Goal
The primary objective of this project is to analyze customer purchasing behavior using the RFM framework to create meaningful customer segments. These segments will help identify key patterns in customer engagement and spending, allowing the business to develop tailored marketing strategies. Additionally, this project aims to analyze sales trends across product categories, channels, and locations, offering deeper insights into the most profitable segments and products. Ultimately, the goal is to optimize customer retention strategies, maximize revenue, and inform decision-making around marketing and product offerings.

## 2. Exploratory Data Analysis

- First, load the required data from the provided Excel sheets. This includes Orders, Product, Location, Customer, and Return (refund) data.
- Ensure all datasets are in DataFrame format.
- Check NA in datasets
- Understanding missing values is essential before moving forward. Use the .isna().sum() method to detect missing values in each dataset.
- In this case, the output is False for all datasets, meaning no missing values were found. However, if missing values were detected, we need to decide on the appropriate handling method (e.g., imputation, removal, etc.).
- Check for duplicate records to avoid redundancy and data inconsistency. Use the .duplicated().sum() method to identify duplicates in each dataset.

## 3. Calculate R, F, M
- Recency: Number of days since the last purchase.
- Frequency: Number of orders placed by the customer.
- Monetary: Total money spent by the customer.


| ID  | Recency | Frequency | Monetary  | r_score | f_score | m_score | RFM Score | Segment               |
|-----|---------|-----------|-----------|---------|---------|---------|-----------|------------------------|
| 0   | 185     | 5         | 5563.560  | 2       | 2       | 5       | 225       | At Risk                |
| 1   | 20      | 9         | 1056.390  | 5       | 5       | 2       | 552       | Potential Loyalist     |
| 2   | 260     | 4         | 1790.512  | 2       | 1       | 3       | 213       | About To Sleep         |
| 3   | 483     | 5         | 5073.975  | 1       | 2       | 5       | 125       | At Risk                |
| 4   | 416     | 3         | 886.156   | 1       | 1       | 2       | 112       | Lost customers         |
| …   | …       | …         | …         | …       | …       | …       | …         | …                      |
| 786 | 83      | 9         | 2110.726  | 3       | 5       | 3       | 353       | Potential Loyalist     |
| 787 | 5       | 4         | 5438.650  | 5       | 1       | 5       | 515       | Promising              |
| 788 | 10      | 8         | 6720.444  | 5       | 4       | 5       | 545       | Champions              |
| 789 | 55      | 12        | 7892.998  | 4       | 5       | 5       | 455       | Champions              |
| 790 | 203     | 4         | 1249.184  | 2       | 1       | 2       | 212       | Hibernating customers  |

This table lists various customer segments and their associated RFM Scores.

*Key Insights from this Table*:

- Lost Customers (RFM Scores like 111, 112): These are customers with the lowest possible recency, frequency, and monetary scores. They haven't purchased in a long time (high recency), have low purchase frequency, and have spent the least amount of money. The business is at risk of losing them entirely.

- Cannot Lose Them (RFM Scores like 113, 114, 115): These customers have slightly better frequency or monetary scores but still show signs of inactivity. They have potential, but immediate action (e.g., re-engagement campaigns) is needed to retain them.

- Potential Loyalists (RFM Scores like 551, 552, 553): These customers have high recency and frequency but spend less than champions. They’ve recently made purchases and are likely to continue buying if nurtured correctly.

- Champions (RFM Scores like 554, 555): These are the top customers. They have purchased recently, purchase frequently, and spend the most. This segment is the most valuable, and the goal is to maintain their loyalty.

*Breakdown by Segment:*
- At Risk (RFM Scores like 125, 225):
Example: The first customer in this table has a recency of 185 days (moderate), with 5 purchases (good frequency), and a high monetary value of 5563.56. The RFM Score = 225, placing this customer in the "At Risk" segment. These customers are valuable but haven’t purchased recently, and the business risks losing them if they aren’t re-engaged.

- Potential Loyalist (RFM Scores like 552, 353):
Example: The second customer has a very recent purchase (20 days ago), a high frequency of 9, but a relatively low monetary value of 1056.39. The RFM Score = 552 places them in the "Potential Loyalist" segment. These customers are buying frequently, but they haven't yet reached the top tier. Upselling or cross-selling may convert them into "Champions."

- About to Sleep (RFM Score like 213):
Example: The third customer has a recency of 260 days, indicating they are nearing inactivity. The frequency is 4, and the monetary value is moderate (1790.51). The RFM Score = 213 places them in the "About to Sleep" segment, showing they are close to becoming inactive and might need re-engagement.

- Lost Customers (RFM Scores like 112):
Example: The fourth customer hasn’t made a purchase in 416 days, has only made 3 purchases, and has a low monetary value. The RFM Score = 112 classifies them as a "Lost Customer." These customers are the hardest to win back but could be targeted with win-back campaigns.

- Champions (RFM Scores like 545, 455):
Example: Customers with high RFM scores across all three categories (e.g., Recency = 10 days, Frequency = 8 purchases, and Monetary = 6720.44) are in the "Champions" segment. They are the best customers, spending frequently and recently. Maintaining their loyalty should be a top priority, perhaps with exclusive rewards or VIP treatment.

## 4. Visualize customer segmentation
### Distribution of Recency, Frequency, Monetary
* In this plot, we want to examine the median recency, frequency, and monetary value accross segments to determine which factor is the most important one among those three.

![Median Recency](https://github.com/caseytientruong/Python-RFM-Analysis/blob/main/median%20recency.png)

The Median Recency by Segment plot shows that the longer it takes for a customer to return to the store (the higher recency score), the less likely he or she is to return at all.  In this plot, we see that recently, the groups of customers are Lost customers, Cannot Lose Them and At Risk. This means, we should focus on marketing strategies, best seller products and customer groups to stimulate more sales to the At Risk group. However, we still see the good amount of customers in Cannot Lose Them group, which are valuable to the company.

![png]([median frequency](https://github.com/caseytientruong/Python-RFM-Analysis/blob/main/median%20frequency.png))

The Median Frequency by Segment plot shows that which group of customers have purchased regularly during a specific period. In this plot, we see groups of Champions, Loyal and Need Attention are the most among other customer groups. This means that it is good to see the most profitable customers in the company.

![png]([median monetary](https://github.com/caseytientruong/Python-RFM-Analysis/blob/main/median%20monetary.png))

The Median Monetary by Segment plot shows customer behavior within the company. This plot aligns well with the Median Frequency by Segment plot because Champions and Loyal customers are customers with the highest monetary and purchase items frequently.

### Pie Chart of customer segmentations

![png](pie chart)

The pie chart shows that there are three most important customer segmentations that the company needs to pay attention to, which are: Potential Loyalist that constitute 14% of all customers, At Risk customers that constitute 12% of all customers and Hibernating customers that constitute 11% of all customers. It is good to see that overall, the company still keep a decent number of potential loyalists. However, seeing that the group of hibernating customers and at risk customers are big, the marketing department can reach out these groups by doing campaign and focus to the group "at risk" to increase customer retention.

### Relationship of RFM Score

![png](recency vs monetary)

Customer who visited more recently generated more revenue compared to those who visited in the distant past. The customers who visited in the recent past are more likely to return compared to those who visited long time ago as most of those would be lost customers. Thus, higher revenue would be associated with most recent visits.

![png](frequency vs monetary)

As the frequency of visits increases, the revenue generated also increases. Customers who visit more frequently are your champion customers, loyal customers or potential loyalists and they drive higher revenue.

![png](frequency vs recency)

Customers with low frequency visited in the distant past while those with high frequency have visited in the recent past. The customers who visited in the recent past are more likely to return compared to those who visited long time ago. Thus, higher frequency would be associated with the most recent visits.

#### Which factor is the most important in RFM score?

Based on the above analysis of the RFM factors, recency is the most important factor to identify customers who are likely to respond to a new offer. Because customers who purchased more recently have a higher chance to purchase again than are customers who purchased further in the past. Once we optimize the recency factor, we can also maximize frequency and monetary score. 

## 5. Analyze Sales Trends 

### Which product categories drive the most revenue? (Monetary)

![png](Sales by product)

In this plot, we observe that Office Supplies is the category that generates the most sales within the company, constitutes over 80% of overall sales in the company, and over 50% of Technology category. This means the company should focus their marketing strategies on Office Supplies to maximize their revenue, and at the same time, doing more advertising campagins or promotions on Technology category as this category is promising in sales.

### Which channels drive the most revenue? (Monetary)

![png](Sales by channel)

The plot above shows that Consumer Channel is the best channel to generate revenue, with over 200000 compared to Corporate with 120000 and Home Office with 70000, which is about 80% of overall sales in the company. Because our best product category is Office Supplies, this indicates our consumers are people who works in corporate jobs or in educational fields, retail or wholesale. This aligns well with the Sales by Product Category plot to help the company build appropriate strategies to focus more on consumer channel more than Home Office and Corporate to maximize the revenue.

### Analyze sales trends over time (Recency vs Monetary)

![png](Sales trend over year)

Based on this plot, we observe a down trend in sales over time from 2014 to 2015 from 10500 to 9000, which is about 20% decrease, then sales has increased from 2015 to 2017 from 9000 to 10000, which is about 10% increase. This indicates that there is a chance that sales will continue to increase from 2017. However, there is a slow increase in sales so we should focus more on most sales genrated product category and customer channel in order to determine the best marketing strategies to maximize our revenue.

![png](Sales trend over month)

Based on this plot, we observe that sales in March, June, September and December are the highest over year, with 7000 is the highest revenue in September. This is because Spring semester in school mostly starts from March to June, while Fall semester in school mostly starts in September, and December is during holidays. This aligns well with the best seller product categeory, which is office supplies that target to students and people who works in corporate jobs. On the other hand, February and October generate the least sales of a whole year.


### Which locations generate the most revenue?

| State      | Sales       |
|------------|-------------|
| Florida    | 21,494.7140 |
| California | 15,773.1628 |
| Michigan   | 11,603.3860 |
| Arizona    | 10,009.8660 |
| Texas      | 8,661.0270  |

Based on the results, there are 5 states that generate the most revenue in the company, which are Florida, California, Michigan, Arizona, and Texas. These locations are among the biggest states in the United States with a large number of populations. Florida has the highest revenue which is nearly 22000, about 17% of overall sales in the United States.

## 6. Recommendations

Based on the RFM analysis conclusion, Recency is the most important factor to focus on because customers who purchased more recently have a higher chance to purchase again than are customers who purchased further in the past. Once we optimize the recency factor, we can also maximize frequency and monetary score.

Although Office Supplies generates the most revenue, technology can be a promising category to generate more sales in the future. The company can consider doing more marketing strategies to advertise related products to technology to target more customer channels. 

In the meantime, consumer channel is the best channel to generate revenue, with over 200000 in total sales. Because our best product category is Office Supplies, this indicates our consumers are people who works in corporate jobs or in educational fields, retail or wholesale. This aligns well with the Sales by Product Category plot to help the company build appropriate strategies to focus more on consumer channel more than Home Office and Corporate to maximize the revenue.

When observing overall sales over time, we observe a slow increase trend from 2017 to present. Thus, we should focus more on most sales genrated product category and customer channel in order to determine the best marketing strategies to maximize our revenue. Furthermore, March, June, September and December are the peak time to generate the most revenue over the year, so we can consider doing campaigns or promotions to maximize sales. 

Lastly, Florida, California, Michigan, Arizona, and Texas are among the best states to generate sales of the United States. Therefore, we can consider pushing best seller product category to target customers during peak time to maximize sales. 

