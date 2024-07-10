#  Exploratory Data Analysis of Cars 

## Background
Background
This project involves performing exploratory data analysis (EDA) on a dataset containing attributes about cars and their associated sales price. It contains almost 12,000 rows and 16 columns. The analysis aims to clean, process, and visualize the data to gain insights and understand the relationships between different variables. The final goal is to perform a linear regression using one of the variables to predict the sales price.

## Executive Summary
The primary objective of this project is to conduct a thorough exploratory data analysis (EDA) on a car dataset using Python. The analysis includes data cleaning, handling missing values, identifying and removing outliers, and visualizing the data using various plots. Additionally, the project aims to explore the relationship between car horsepower (HP) and sales price (MSRP) through linear regression. The results will provide insights into the dataset's structure and highlight key patterns and relationships.

## Goals of Analysis
  ##### • Create the EPL_Standings Function: Retrieve EPL match data from online resources.
  ##### • Process Match Data: Compute crucial statistics for each team.
  ##### • Display Updated Standings: Rank teams by points per match and additional tie-breaking metrics.
  ##### • Ensure Data Accuracy: Efficiently handle data from the most recent three EPL seasons.

## Methodology
##### •Data Retrieval: The function extracts EPL match results for the given season from web sources. It covers the three most recent seasons:   2021/22, 2022/23, and 2023/24.
##### •Data Cleaning: Standardizes date formats and column names across different seasons for consistency.
##### • Data Transformation: Filters data to include only matches up to the specified date.
##### • Data Aggregation: Merges home and away match results, calculating wins, losses, draws, goals, points, and other relevant statistics.
##### • Data Sorting: Orders the final standings by points per match, wins, goals per match, and goals allowed per match.

## Key Insights
##### • Performance Metrics: The function calculates key metrics such as points per match, point percentage, goals scored per match, and goals allowed per match.
##### • Team Comparison: Provides detailed comparisons of team performances, offering clear standings based on multiple criteria.
##### • Dynamic Data Handling: The function can dynamically update standings with current season data as new matches occur.


## Recommendations
##### • Regular Data Validation: Continuously validate and clean the dataset to maintain accuracy.
##### • Expand Function Features: Incorporate additional features, such as multi-season trend analysis or player-specific performance metrics.
##### • Develop a User-Friendly Interface: Create an accessible interface for non-technical users to easily view and interpret league standings.
