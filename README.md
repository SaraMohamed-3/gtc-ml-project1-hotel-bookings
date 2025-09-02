# gtc-ml-project1-hotel-bookings
This project provides a step-by-step Jupyter Notebook pipeline for cleaning and preprocessing the hotel_bookings.csv dataset, preparing it for machine learning tasks such as predicting booking cancellations.
The notebook is structured into three phases:

Phase 1: Exploratory Data Analysis (EDA) & Data Quality Report
This phase focuses on understanding the raw dataset and identifying potential data quality issues.
Data Overview: Load the dataset and examine its structure using .info() and .describe().
Missing Value Analysis: Visualize missing data patterns with a heatmap.
Outlier Detection: Use boxplots and the Interquartile Range (IQR) method to identify aoutliers in numerical columns like adr and lead_time.

Phase 2: Data Cleaning
Here, we address the issues discovered during EDA.
Handling Missing Values:
company and agent: Replace missing values with 0 (no ID).
children: Fill missing values with the median.
country: Replace missing values with "Unknown".
Removing Duplicates: Drop exact duplicate rows.
Outlier Treatment: Cap extreme adr values at 1000 to reduce skewness.

Phase 3: Feature Engineering & Preprocessing
This step prepares the data for modeling.
New Features:
total_guests = adults + children + babies
total_nights = stays_in_weekend_nights + stays_in_week_nights
is_family = "Yes" if children + babies > 0 else "No"
Categorical Encoding:
Apply one-hot encoding for low-cardinality features (e.g., meal, market_segment).
Frequency Encoding for high-cardinality features (e.g., country).

Preventing Data Leakage: Drop reservation_status and reservation_status_date since they wouldn’t be available at prediction time.
Final Dataset Split: The cleaned dataset is divided into training and testing sets.

How to Use:
1. Install dependencies: pip install pandas numpy seaborn scikit-learn matplotlib
2. Place the hotel_bookings.csv file in the same directory as the notebook.
3. Open and run the notebook: jupyter notebook project1_hotel_bookings.ipynb
