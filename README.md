# Smart Cart Analytics

### The Problem Area
Grocery & Food Delivery: The grocery and food delivery business has been growing rapidly in recent years, with many customers adopting this new habit during the COVID 19 pandemic and continuing to buy food online in a post COVID world.

**Challenges and opportunities to address:**
1. **Predicting Future Purchase Behavior:** With evolving customer habits, past purchase data may not be a reliable predictor of future behavior.
2. **Demand Forecasting and Inventory Demand:** Industry growth, shifts in customer loyalty, and habits can influence demand unpredictably.
3. **Increasing Order Value:** Customers might be more open to suggestions but can also be unpredictable in their purchasing habits.

### The User
This project's insights will benefit business owners, investors, and stakeholders within the grocery and food delivery ecosystem.

**Advantages for the business:**
- Enhanced sales forecasting and resource allocation.
- Optimized inventory management, reducing costs related to stockouts or overstock.
- Increased revenue through effective cross-selling, improving customer loyalty and satisfaction.

### The Big Idea
Machine learning offers robust methodologies to address the identified challenges:

- **Predicting Future Purchase Behavior:** Utilizing Recommendation Systems, Clustering, Classification, and Sequence Prediction Models.
- **Demand Forecasting:** Implementing Time Series Forecasting, Regression Analysis, and Deep Learning Models.
- **Cross-Selling Products:** Leveraging Association Rule Mining, Collaborative Filtering, and Content-Based Filtering.

### The Impact
The societal and business implications are significant:

- **Demand Forecasting:** Inaccurate forecasting leads to approximately $1.1 trillion in global retailer costs annually. Improved predictions can slash these costs and boost sales by 10-20%.
- **Seasonal Forecasting:** Forecasting errors can incur up to 30% in lost sales during peak periods. Environmentally, unsold inventory, like in the fashion sector, contributes to substantial waste and CO2 emissions.
- **Cross-Selling:** Amazon reports that 35% of its revenue comes from its recommendation engine, a strategy that can translate into billions of dollars for major e-commerce platforms.

## Dataset Overview
The dataset, sourced from Instacart's "The Instacart Online Grocery Shopping Dataset 2017", part of the Kaggle community competition in 2017, comprises over 3 million grocery orders from more than 200,000 users. It includes detailed order sequences, product information, and user purchase times.

## Project Organization

| File | Description |
| ------ | ----------- |
| README.md | The main README document for developers using this project |
| Presentation_EDA.pdf | Initial presentation of the project including EDA |
| data | Instacart Dataset (https://www.kaggle.com/competitions/instacart-market-basket-analysis/). |
| notebooks | Project Notebook |
| app | ML model |

EDA.ipynb


## Table of contents

- Instacart Dataset 
- Data Download, Cleaning & EDA
- Modelling
- Conclusions
- Citation

### Instacart Dataset (Data Dictionary)

#### `aisles.csv` - numeric and categorical data
| Column | Description |
| ------ | ----------- |
| aisle_id | Unique ID for aisle |
| aisle | The name of the aisle |

#### `departments.csv` - numeric and categorical data
| Column | Description |
| ------ | ----------- |
| department_id | Unique ID for department |
| department | The name of the department |


#### `order_products__train.csv` - numeric data
| Column | Description |
| ------ | ----------- |
| order_id | Unique ID for order |
| product_id | Unique ID for a product |
| add_to_cart_order | Order in which each product was added to cart |
| reordered | Indicator if the product was reordered (1) or not (0) |

This file is typically used for training machine learning models. It contains data about the orders, specifically which products were purchased in each order.

#### `order_products__prior.csv` - numeric data
| Column | Description |
| ------ | ----------- |
| order_id | Unique ID for order |
| product_id | Unique ID for a product |
| add_to_cart_order | Order in which each product was added to cart |
| reordered | Indicator if the product was reordered (1) or not (0) |

#### `orders.csv` - numeric data
| Column | Description |
| ------ | ----------- |
| order_id | Unique ID for order |
| user_id | Unique ID for a user |
| eval_set | Which evaluation set this order belongs in |
| order_number | The order sequence number for this user |
| order_dow | The day of the week the order was placed on |
| order_hour_of_day | The hour of the day the order was placed |
| days_since_prior_order | Days since the last order was placed |

#### `products.csv`
| Column | Description |
| ------ | ----------- |
| product_id | Unique ID for a product |
| product_name | The name of the product |
| aisle_id | Aisle ID |
| department_id | Department ID |

## Data Download, Cleaning & Exploratory Data Analysis

In our project Smart Cart Analytics, we tackle Exploratory Data Analysis (EDA) in three main phases. First, we download the dataset from Instacart's detailed big database of customer orders. Secondly, we check the dataset for any duplicates, missing entries, and errors to make sure the data is accurate.

Next, we move into a detailed examination of the data, using graphs and charts to spot trends and investigate how different factors, like reorder rates and peak ordering times, interact. We combine Product, Aisles and Departments data sets for its convenience.

Key takeaways from our EDA include:

Items added to the cart in the first sequels are often bought again later.
The highest number of repeat purchases occurs at certain regular times, indicating the presence of shopping habits.
Products from certain areas of the store are bought again more often, showing what customers prefer.
As customers keep ordering over time, they tend to focus on a smaller set of familiar products.
The chance of buying a product again goes down as the number of different items in the cart increases, likely due to the greater variety of choices.
These early observations are crucial, forming the basis for our predictive models and helping us make smart decisions to improve customer interaction and optimize inventory on Instacart.

EDA.Part 2
We created 2 datasets separated per prior/train orders and combined it with the product information files. Thus,we obtained final versions of dataframe that we will be using for further data analysis and modeling. 
We continued with the EDA focusing in aisles and department distributions, looking into most frequent and most reordered items. Analyzed items reorder probability together with its sequence in the list and frequency. Found Top 25 Products with Highest Reorder Ratio from the top 25% most frequently bought products.
As a part of EDA, we explored corelations of the variables with the correlation matrix.
As for Statistical Analysis- premodeling, we ran a logistic regression and built classification report together with the confusion matrix.
Train score: 0.6480956366068937
Test score: 0.6477300631220119

FOR NOT REORDERED:

Precision for class 0 (not reordered) is 0.61, meaning that when the model predicts a product is not reordered, it is correct 61% of the time.

Recall for class 0 is 0.34, indicating that the model correctly identifies 34% of the actual not reordered cases.

F1-score for class 0 is 0.44, which is a weighted average of precision and recall for class 0, suggesting that the model is not performing well at identifying not reordered cases.

FOR REORDERED:

Precision is 0.66, meaning the model's prediction of a product being reordered is correct 66% of the time.

Recall is 0.85, showing that the model identifies 85% of all actual reordered cases.

F1-score is 0.74, indicating a relatively higher performance of the model in identifying reordered cases compared to not reordered cases.

Accuracy of the model is 0.65, meaning it correctly predicts the reordered status for 65% of the products overall.

SUMMARY:

The model is better at identifying products that will be reordered than those that will not. This could be because there are more reordered instances in the dataset (evidence of class imbalance), or the features are more predictive for the reordered class. The relatively high number of False Positives (products predicted as reordered but actually not) suggests that the model might be erring on the side of predicting reorder.

This could be addressed by looking into the model's threshold for classification or gathering more distinguishing features.

The accuracy is moderately good, but there is definitely room for improvement, especially in terms of precision and recall for the not reordered class.

Further analysis is needed as the most part of the data is in numerical format. Next step would be run a bag of words in order to convert non-numeric values and include it into our model.

## Preprocessing:
Dropping column not needed for the modelling- aisle_id’, 'department_id','aisle','department’, 'product_id','user_id’
Y – Reordered variable
Vectorization of the Product column using Vectorizer - Bag of words method

## Modeling

Several ML models were built including: Logistic Regression model, Decision Tree,KNN Classifier, RandomForest and SVC.
Tuning was done with Hyperparameter optimization, ML Pipelines – Grid searchCV, pipeline design and Scaling (StandardScaler)

SVC and optimized Random Forest have shown the best performance amongst the other models - 82.45%/82.43% and 78.22%/77.61% respectively.

Market Basket analysis with Apriori algorythm was also performed to develop a grocery recommender system.

Recommendation algorithm together with the reordered prediction, will help the company to forecast what products a customer is likely to purchase in their next order.

## Conclusion

Machine learning models have become increasingly valuable in predicting customer behavior in online grocery shopping, providing insights that can drive sales, enhance customer experience, and streamline operations.

ML models in online grocery retail can lead to more effective business strategies, improved customer satisfaction, and increased revenue.

### Built With

This section should list any major frameworks/libraries used to bootstrap your project. Leave any add-ons/plugins for the acknowledgements section. Here are a few examples.

* [![Python][python.org]][Python-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Daria Vasylieva -  daria.vasylieva@gmail.com

Project Link: [https://github.com/dariiavas/Capstone](https://github.com/dariiavas/Capstone)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Citation

@misc{instacart-market-basket-analysis,
    author = {jeremy stanley, Meg Risdal, sharathrao, Will Cukierski},
    title = {Instacart Market Basket Analysis},
    publisher = {Kaggle},
    year = {2017},
    url = {https://kaggle.com/competitions/instacart-market-basket-analysis}
}