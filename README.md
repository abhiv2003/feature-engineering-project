# CCMCA311: Feature Engineering Mini Project

This project focuses on the complete feature engineering pipeline applied to an e-commerce dataset (Maven Fuzzy Factory). The goal is not model training, but to clean, integrate, transform, and reduce the data to make it ready for machine learning analysis, as per the project requirements.

## 1. Project Objective
The main objective of this project is to apply the four major stages of feature engineering:
* Data Cleaning
* Data Integration
* Data Transformation
* Data Reduction

## 2. Dataset Source
* **Name:** Maven Fuzzy Factory E-commerce Dataset
* **Description:** This dataset contains real e-commerce data from a fictional company, split across 6 CSV files (`orders.csv`, `sessions.csv`, `products.csv`, etc.).

## 3. Steps Performed

1.  **Data Cleaning:**
    * Handled 80,000+ missing values in `sessions` table (e.g., `utm_source`) by imputing them with 'none'.
    * Checked for duplicates (found 0).
    * Checked for noisy data (found no unrealistic values like negative prices).
    * Detected outliers using Box Plots (e.g., `items_purchased`) and retained them as valid business data.

2.  **Data Integration:**
    * Merged 6 different CSV files (like `orders`, `order_items`, `products`) using `pd.merge()` on common keys (`order_id`, `product_id`) to create a single master table.

3.  **Data Transformation:**
    * **Encoding:** Applied One-Hot Encoding to the `device_type` column.
    * **Standardization:** Applied Z-score Scaling (StandardScaler) to the `price_usd_order` column.
    * **Discretization (Binning):** Converted the `order_hour` (0-23) into 4 meaningful categories ('Night', 'Morning', 'Afternoon', 'Evening').

4.  **Data Reduction:**
    * Removed all unnecessary ID columns (`order_id`, `user_id`, etc.).
    * Used a Correlation Heatmap to find and drop highly redundant features (dropped `cogs_usd_order` due to its 0.98 correlation with `price_usd_order`).

## 4. Key Results
* The final output is a single, clean dataset (`final_cleaned_data`) with 6 optimized features, ready for model training.

## How to Run
1.  Open `feature_engineering.ipynb` in Google Colab.
2.  The notebook contains all the code and comments for the 4 stages.
3.  The `theory_report.pdf` contains a detailed theoretical explanation of each step.
