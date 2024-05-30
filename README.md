# Data Analysis and Visualization Script

This an overview of a data analysis script that performs data cleaning, visualization, clustering, and association rule mining. The script is designed to work with user-provided CSV files and utilizes various R libraries for its operations.

## Step 1: Data Cleaning

1. **Loading the Dataset**: The script begins by prompting the user to input the path to the CSV dataset. It reads the dataset and displays its structure to give an overview of the data.

2. **Cleaning the Data**:
   - **Handling Missing Values**: Rows containing missing values are removed to ensure data integrity.
   - **Standardizing Column Names**: Column names are converted to lowercase for consistency.
   - **Removing Empty Rows and Columns**: Any remaining empty rows and columns are eliminated.
   - **Removing Duplicate Rows**: Duplicate rows are removed to prevent redundancy.

## Step 2: Data Visualization

1. **Total Spending by Payment Type**: A pie chart is created to compare the total spending between different payment types (e.g., cash vs. credit).

2. **Number of Transactions by Payment Type**: Another pie chart compares the number of transactions made with different payment types.

3. **Spending per Age Group**: A plot is generated to show the total spending by different age groups, providing insights into spending behavior across ages.

4. **Spending per City**: A bar plot illustrates the total spending in different cities, highlighting the cities with the highest and lowest expenditures.

5. **Distribution of Total Spending**: A box plot displays the distribution of total spending, offering a visual representation of spending patterns and outliers.

## Step 3: Clustering

1. **User Input for Number of Clusters**: The user is prompted to enter the desired number of clusters for the k-means clustering algorithm.

2. **K-Means Clustering**: The script performs k-means clustering on the data, grouping customers based on age and total spending. The clusters are displayed, and a table is created to show each customer's cluster assignment along with their age and total spending.

## Step 4: Association Rules

1. **User Input for Minimum Support and Confidence**: The user is asked to specify the minimum support and confidence levels for the Apriori algorithm.

2. **Apriori Algorithm**: The script applies the Apriori algorithm to identify association rules within the transaction data. It displays the discovered rules based on the specified support and confidence thresholds.

## Saving the Cleaned Dataset

The cleaned dataset is saved back to the specified CSV file path, ensuring that the processed data is available for future use.

---

This script analyzing customer transaction data, offering valuable insights through various data cleaning, visualization, clustering, and association rule mining techniques. The use of interactive user inputs allows for flexible and customized analysis based on specific requirements.
