# Smart Cart Analytics

## Sprint 1: Project Initiation

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

## Modeling

## Conclusion


## Citation

@misc{instacart-market-basket-analysis,
    author = {jeremy stanley, Meg Risdal, sharathrao, Will Cukierski},
    title = {Instacart Market Basket Analysis},
    publisher = {Kaggle},
    year = {2017},
    url = {https://kaggle.com/competitions/instacart-market-basket-analysis}
}