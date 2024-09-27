![image](https://github.com/user-attachments/assets/a4a20d5b-9900-48d6-8a6a-3f2cbc1d3219)# Amazon-Monitor-Market-Analysis

## Project Overview

This project performs an in-depth analysis of Amazon product data, specifically focusing on computer monitors. 

**Objective:**

The primary goal is to extract meaningful insights from the data to understand market trends, customer behaviour, and product segmentation. This analysis provides valuable information for business decision-making, such as pricing strategies, product development, and marketing campaigns.

**Data Source:**

The project utilizes a dataset of Amazon product information for computer monitors obtained from Kaggle. The specific dataset used can be found [Here](https://www.kaggle.com/datasets/durjoychandrapaul/amazon-products-sales-monitor-dataset). The dataset contains attributes like brand, price, rating, screen size, and aspect ratio.

## Tools Used

This project leverages the following tools for data analysis and visualization:

* **Programming Language:** Python 3
* **Libraries:**
    * Pandas: Data manipulation and analysis
    * NumPy: Numerical computations
    * Matplotlib: Static, interactive, and animated visualizations
    * Seaborn: Statistical data visualization
    * IPython: Interactive computing in Jupyter Notebooks
* **Environment:** Google Colab [link here](https://colab.google/)
* **Data Visualization:**
    * Histograms
    * Bar plots
    * Box plots
    * Scatter plots
    * Line plots
    * Heatmaps
* **Data Analysis Techniques:**
    * Descriptive statistics
    * Exploratory data analysis (EDA)
    * Correlation analysis
    * Segmentation
    * Trend analysis
    * Competitor analysis
 

  ## Methodology

This project follows a structured approach to analyze the Amazon product data, encompassing the following steps:

### Data Collection and Preprocessing:**

* The data was loaded and preprocessed using Pandas:

```python
import pandas as pd

Read the uploaded CSV file

df = pd.readcsv('extractedproductinfoamazon.csv')
```

### Checking for missing values and data types

```python
print("Missing values:\n", df.isnull().sum())
print("\nData types:\n", df.dtypes)
```

### Converting 'Price' and 'Rating' columns to numeric

```python
df['Price'] = pd.to_numeric(df['Price'], errors='coerce')
df['Rating'] = pd.to_numeric(df['Rating'], errors='coerce')
```

### Extracting numeric part of 'Screen Size'

```python
df['Screen Size'] = df['Screen Size'].str.extract('(\d+.?\d*)').astype(float)
```

Removing duplicates

```python
df.drop_duplicates(inplace=True)
``

Handling missing values by filling

```python
df.fillna({'Rating': df['Rating'].mean(), 'Price': df['Price'].median()}, inplace=True)
df.dropna(subset=['Screen Size'], inplace=True)
```

## Descriptive Analysis: 

Calculating summary statistics, identifying key metrics, and visualizing the distributions of important variables.

```python
numerical_summary = df[['Price', 'Rating', 'Screen Size']].describe()
print("Numerical Descriptive Statistics:\n", numerical_summary)

print("\nVariance of Price:", df['Price'].var())
print("Variance of Rating:", df['Rating'].var())
print("Variance of Screen Size:", df['Screen Size'].var())

print("\nMedian of Price:", df['Price'].median())
print("Median of Rating:", df['Rating'].median())
print("Median of Screen Size:", df['Screen Size'].median())
```

### Categorical Descriptive Statistics

```python
# Frequency of Brands
brand_count = df['Brand'].value_counts()
print("\nFrequency of Brands:\n", brand_count)

# Frequency of Aspect Ratios
aspect_ratio_count = df['Aspect Ratio'].value_counts()
print("\nFrequency of Aspect Ratios:\n", aspect_ratio_count)
```

## Visualizing Key Descriptive Measures

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Histogram for numerical features
plt.figure(figsize=(14, 6))

plt.subplot(1, 3, 1)
sns.histplot(df['Price'], bins=20, kde=False, color='blue')
plt.title('Price Distribution')

plt.subplot(1, 3, 2)
sns.histplot(df['Rating'], bins=20, kde=False, color='green')
plt.title('Rating Distribution')

plt.subplot(1, 3, 3)
sns.histplot(df['Screen Size'], bins=20, kde=False, color='red')
plt.title('Screen Size Distribution')

plt.tight_layout()
plt.show()
```
![image](https://github.com/user-attachments/assets/763ae7e1-42f4-42d0-91a1-8787edfa20f7)


### Categorical Data Visualization

![image](https://github.com/user-attachments/assets/40feb5c4-3a16-4a2e-9555-b74ebd1bd04d)


![image](https://github.com/user-attachments/assets/fd164583-3a8d-436e-8a93-14165d7d3f26)


## Key Insights from Descriptive Analysis

- 1. The average price of the monitors is $245.65, with a median price of $189.43.
  2. The average rating of the monitors is 4.33, with most ratings falling between 1.00 and 5.00.
  3. The most common screen size is 27.0 inches
  4. The most frequent aspect ratio is '16:9'.
  5. LG has the highest number of monitor products in the dataset.

     
## Exploratory Data Analysis (EDA):

Exploring the relationships between features, identifying patterns, and detecting outliers.


![image](https://github.com/user-attachments/assets/262e0d38-2fba-4d91-9f15-aae76b9d349c)


![image](https://github.com/user-attachments/assets/3ae661bf-5390-4049-98ef-032cfd195587)


![image](https://github.com/user-attachments/assets/c8057da7-b382-40ec-b22a-cf7e1295966b)


![image](https://github.com/user-attachments/assets/0b4e652f-c774-4450-b65a-3aaa6131a939)


![image](https://github.com/user-attachments/assets/3a3ad8bf-b3c8-491c-a86d-182b69b55a49)


### Product Segmentation:
Grouping products based on price, screen size, and rating for targeted analysis.


![image](https://github.com/user-attachments/assets/4e98bd41-cb8c-419f-952e-4747824b3013)


![image](https://github.com/user-attachments/assets/b28ce106-956f-4dc4-97b7-f1fafd70eb89)

### Rating Segmentation

![image](https://github.com/user-attachments/assets/4674df28-7359-4ea1-8269-5669b254f751)

### Combining Multiple Segments


![image](https://github.com/user-attachments/assets/c45694ea-82a8-4f32-8e0b-680f893832d8)


### Customer Behavior Analysis:
Analyzing purchase history, frequency, and spending patterns of customers.

![image](https://github.com/user-attachments/assets/d8ac497b-7737-44bd-b671-09267f75ccf4)

![image](https://github.com/user-attachments/assets/32624a6e-0703-4626-a8a0-aa206ad5b50d)


### Purchase Frequency Analysis

![image](https://github.com/user-attachments/assets/ac5e9b0f-c54b-4acb-ac2f-dceb0f84b895)

![image](https://github.com/user-attachments/assets/3d4e8926-2325-46ba-922c-9b55ee2e3f5a)

![image](https://github.com/user-attachments/assets/572804c4-7962-46a1-adbe-76f552aef9da)


## Market Trends and Opportunities Analysis

![image](https://github.com/user-attachments/assets/6dff0e72-f5fb-4763-b8d1-35c6796386e3)

![image](https://github.com/user-attachments/assets/4b041f09-6d48-40d5-b0d5-98e40d685b3f)

![image](https://github.com/user-attachments/assets/a4db3efa-b4f0-4be8-ab52-2aa73e923d5a)

![image](https://github.com/user-attachments/assets/424d3af3-85a7-4177-b4d0-74f7af14e6cc)


## Key Findings:

The analysis provides valuable insights into market trends, customer preferences, and product segmentation, including:

* Identification of top brands by product count and customer preference.
* Understanding the relationship between price, rating, and screen size.
* Segmentation of products into different categories for targeted analysis.
* Insights into customer behaviour, including purchase frequency and spending patterns.
* Analysis of sales growth trends over time.
* Evaluation of competitor performance and market positioning.

## Potential Applications:

The insights generated from this project can be utilized for:

* Pricing optimization.
* Product development and improvement.
* Targeted marketing campaigns.
* Competitive analysis and strategy.
* Market trend identification and opportunity assessment.

# Product Recommendations:

### Focus on popular screen sizes and aspect ratios: 
The analysis revealed the most common screen sizes and aspect ratios. Consider focusing on offering products with these specifications to cater to the majority of customer preferences. 

### Offer competitive pricing:
Analyze the pricing strategies of your competitors (as done in the Competitor Analysis section) to ensure your products are priced competitively within the market. Consider adjusting prices for segments like "Low Price" to further attract budget-conscious customers. 

### Highlight highly-rated products: 
Promote products with high average ratings, as customer satisfaction is a key factor in purchasing decisions. You can filter your DataFrame df to identify products with ratings above a certain threshold

### Expand product offerings: 
Identify market gaps or underserved segments based on your analysis. For example, if there is a demand for monitors with specific features (like curved screens or high refresh rates) that are not adequately addressed by current offerings, consider expanding your product line to cater to these needs. You can analyze customer purchase history and preferences to understand these unmet needs.

## Marketing and Sales Recommendations:

### Targeted advertising: 
Tailor marketing campaigns to specific customer segments based on age, location, and purchasing behaviour. Utilize the customer segmentation data to identify potential customers for different product categories. For example, target younger customers with gaming monitors and professionals with larger, higher-resolution monitors. You can filter the customer_data DataFrame based on age, gender, and location.

### Promotions and discounts: 
Consider offering promotions and discounts to stimulate sales during periods of low demand. You can identify these periods using the sales growth analysis (e.g., months with lower total sales).
Product bundling: Explore opportunities for product bundling to increase average order value. For example, offer bundles of monitors with complementary accessories like keyboards, mice, or webcams. Analyze purchase history to identify products commonly bought together.

### Customer loyalty programs: 
Implement customer loyalty programs to reward repeat customers and foster brand loyalty. You can use customer purchase frequency analysis to identify frequent customers.
Enhance customer experience: Focus on providing excellent customer service to build a positive brand reputation. Encourage customer reviews and feedback to identify areas for improvement.

😄
💻

|heading|
