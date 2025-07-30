Analysing Customer Behaviour for E-commerce Insights
GitHub Repo Link: 
Simulate an e-commerce dataset, analyse customer behaviour, and build a model to predict churn (whether a customer will stop using the platform). Then store the data in Elasticsearch for fast querying and visualization.

1.  Data Generation
We use the Faker library to generate fake customer and session data to simulate a real e-commerce environment.
Customers: Generate 10,000 customers with:
        1.	customer_id
        2.	age
        3.	gender
        4.	location
        5.	customer_since (when they joined)
Sessions: Generate 100,000 browsing/purchase sessions with:
        1.	Session times
        2.	Pages viewed
        3.	Products added and purchased
        4.	device_type, payment_method
        5.	churned status = if they haven’t purchased in 60+ days

2. Data Cleaning & Basic EDA (Exploratory Data Analysis)
Clean the data:
•	Check data shape and types: df.info()
•	Handle missing values: df.isnull().sum()
•	Remove duplicates: df.duplicated().sum()
Add new columns:
session_duration, days_since_last_active, spend_per_product
These features help understand customer behavior better:
•	session_duration: Are long sessions more likely to lead to purchases?
•	days_since_last_active: Helps identify inactivity = possible churn.
•	spend_per_product: Shows how much they're spending per item.
3. Data Visualization
Using seaborn and matplotlib, we visualize:
•	Churn distribution: To see how many customers churned.
•	Total Spend vs. Churn: Do churned customers spend less?
•	Session Duration by Churn: Are churned users spending less time?

4. Predictive Modelling
Random Forest Classifier was used to predict churn based on customer behavior.
Features used: age, session_duration, pages_viewed, products_added_to_cart,  products_purchased, total_spent

These features show how active and valuable a customer is:
•	More purchases, time spent, pages viewed implies that it is likely not churned
•	High spenders are more valuable: predict behavior more effectively
Steps:
1.	Train/test split
2.	Train Random Forest
3.	Predict churn
4.	Evaluate with classification report (precision, recall, F1-score)

5.Big Data Tool – Elasticsearch
Elasticsearch was used to:
•	Upload and store the dataset
•	Run fast queries and aggregations
Why Elasticsearch?
•	Handles large datasets quickly
•	Allows fast aggregations (e.g., "how many customers are male/female?")
•	Useful for dashboards with Grafana
