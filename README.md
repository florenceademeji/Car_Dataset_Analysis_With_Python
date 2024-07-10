#  Exploratory Data Analysis of Cars 

## Background
Background
This project involves performing exploratory data analysis (EDA) on a dataset containing attributes about cars and their associated sales price. It contains almost 12,000 rows and 16 columns. The analysis aims to clean, process, and visualize the data to gain insights and understand the relationships between different variables. The final goal is to perform a linear regression using one of the variables to predict the sales price.

## Executive Summary
The primary objective of this project is to conduct a thorough exploratory data analysis (EDA) on a car dataset using Python. The analysis includes data cleaning, handling missing values, identifying and removing outliers, and visualizing the data using various plots. Additionally, the project aims to explore the relationship between car horsepower (HP) and sales price (MSRP) through linear regression. The results will provide insights into the dataset's structure and highlight key patterns and relationships.

## Goals of Analysis
  ##### • Create and Clean DataFrame 
  Read the dataset and clean it by removing unnecessary columns, handling missing values, and removing duplicates.
  
  ##### • Data Exploration 
  Generate summary statistics and visualizations to understand the distribution and relationships between variables.
  
  ##### • Identify and Handle Outliers 
  Use box plots to identify outliers and remove them to improve data quality.
  
  ##### • Visualize Data 
  Create various plots to visualize the distribution of key variables and the relationships between them.
  
  ##### • Perform Linear Regression
  Investigate the linear relationship between horsepower (HP) and sales price (MSRP) and evaluate the model's performance.

## Methodology
##### • Data Retrieval: Read the P5-CarData.csv file into a Pandas DataFrame.
##### • Data Cleaning: Remove unnecessary columns, handle missing values, and remove duplicate rows.
##### • Descriptive Statistics: Generate summary statistics for the dataset to understand its structure.
##### • Outlier Detection and Removal: Use box plots and the IQR method to identify and remove outliers.
##### • Data Visualization: Create visualizations, including histograms, box plots, bar plots, and pair plots, to explore data distributions and relationships.
##### • Linear Regression: Perform linear regression to explore the relationship between horsepower (HP) and sales price (MSRP) and evaluate the model's performance.

## Key Insights
##### •	Maximum Horsepower (HP): The dataset contains cars with a maximum horsepower of 1001 HP.
##### •	Minimum City MPG: The minimum city MPG in the dataset is 7 MPG.
##### •	Maximum Highway MPG: The maximum highway MPG in the dataset is 354 MPG.
##### •	Maximum Price (MSRP): The maximum sales price (MSRP) in the dataset is $2,065,902.
##### •	Outliers: Identified and removed outliers based on the IQR method to improve data quality.
##### •	Data Relationships: Visualizations reveal key relationships and distributions in the dataset, aiding in understanding car attributes and their impact on sales price.
##### •	Linear Regression: Initial linear regression between HP and MSRP showed an R-squared value of approximately 0.438, indicating a moderate relationship.

## Recommendations
##### • Regular Data Validation: Continuously validate and clean the dataset to maintain accuracy and reliability.
##### • Expand Analysis: Incorporate additional features and variables in the analysis, such as car make and model, to explore their impact on sales price.
##### • Improve Linear Regression Model: Consider removing additional outliers and exploring non-linear models to improve the predictive performance.
##### • Develop User-Friendly Interface: Create an accessible interface for non-technical users to view and interpret the analysis results easily.
