# Google Play Store Analysis

## 📌 Project Overview

This project performs an end-to-end analysis of the Google Play Store ecosystem using Python. The analysis focuses on data cleaning, exploratory data analysis, app categories, ratings, installations, pricing, and sentiment analysis of user reviews.

The objective is to identify patterns in the app market and generate data-driven insights that could help developers make better decisions when launching or improving an application.

## 🎯 Objectives

- Clean and prepare real-world Google Play Store datasets
- Analyse app distribution across categories
- Study app ratings and category-level performance
- Analyse app size and installation trends
- Compare free and paid applications
- Estimate potential revenue by category
- Perform sentiment analysis on user reviews
- Analyse sentiment across app categories
- Generate actionable recommendations for app developers

## 🛠️ Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- TextBlob / VADER
- Plotly
- Jupyter Notebook

## 📂 Datasets

The project uses two datasets:

1. Google Play Store Apps dataset
2. Google Play Store User Reviews dataset

The datasets contain information such as:

- App name
- Category
- Rating
- Reviews
- Size
- Installs
- Type
- Price
- Content Rating
- Genres
- User reviews
- Sentiment

## 🔍 Analysis Performed

### 1. Data Cleaning

- Handled missing values
- Removed duplicate applications
- Converted `Installs` into numeric format
- Converted `Price` into numeric format
- Corrected data types
- Identified inconsistent and invalid values

### 2. Category Analysis

- Analysed the number of applications in each category
- Identified highly saturated categories
- Visualised category distribution

### 3. Ratings Analysis

- Analysed the distribution of application ratings
- Calculated average ratings by category
- Identified categories with higher average ratings

### 4. Size and Installation Analysis

- Compared application size with installation counts
- Investigated relationships between app size and popularity

### 5. Pricing Analysis

- Compared free and paid applications
- Analysed the distribution of paid app prices
- Estimated potential revenue by category

### 6. Sentiment Analysis

User reviews were classified into:

- Positive
- Negative
- Neutral

Sentiment was analysed across different app categories.

### 7. Interactive Visualization

Plotly was used to create interactive visualisations for exploring important trends.

## 📊 Key Insights

The final notebook contains data-driven insights covering:

- Most saturated app categories
- Categories with stronger ratings
- Installation trends
- Free vs paid applications
- Pricing patterns
- User sentiment
- Opportunities for new applications

## 💡 Business Recommendations

The analysis concludes with recommendations for developers planning to launch a new application, based on category competition, ratings, installations, pricing and user sentiment.

## 🚀 How to Run

Clone the repository:

```bash
git clone https://github.com/Sasikumar021/OIBSIP.git
