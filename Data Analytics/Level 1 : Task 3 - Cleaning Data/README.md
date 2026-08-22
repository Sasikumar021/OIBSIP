# 🧹 Amazon Sales Data Cleaning & Exploratory Analysis

## 📌 Project Overview

This project demonstrates a complete **data cleaning and exploratory analysis workflow using Python** on an Amazon product and sales dataset.

The objective is to transform an uncleaned dataset containing product information, ratings, review counts, pricing, promotional indicators, availability details, and product URLs into a **clean, consistent, and analysis-ready dataset**.

The project covers practical data-quality tasks including **missing-value handling, duplicate detection and removal, text standardization, data-type conversion, outlier detection, outlier treatment, and exploratory data analysis**.

---

## 🎯 Project Objectives

* Inspect the structure and quality of the raw dataset.
* Identify missing values and duplicate records.
* Standardize column names.
* Clean and standardize text-based fields.
* Convert suitable columns into appropriate data types.
* Handle missing categorical and numerical values.
* Detect numerical outliers using the **IQR method**.
* Apply outlier capping where appropriate.
* Compare data quality before and after cleaning.
* Create meaningful exploratory visualizations.
* Identify products with high numbers of reviews.
* Analyze the relationship between product ratings and review counts.
* Examine ratings by Best Seller status.
* Export the cleaned dataset for further analysis.

---

## 📊 Dataset

The dataset contains **Amazon product information** collected from product listings.

The original dataset contains:

* **8,127 rows**
* **16 columns**

The raw dataset includes product titles, ratings, review counts, purchase activity, pricing information, promotional indicators, availability information, product URLs, and collection timestamps.

### Dataset Columns

| Column                     | Description                                                     |
| -------------------------- | --------------------------------------------------------------- |
| `Title`                    | Product title/name                                              |
| `Rating`                   | Product rating represented as text such as `4.6 out of 5 stars` |
| `Number_of_reviews`        | Number of customer reviews                                      |
| `bought_in_last_month`     | Approximate number of products purchased in the previous month  |
| `Current/discounted_price` | Current or discounted product price                             |
| `Price_on_variant`         | Price information associated with a product variant             |
| `Listed_price`             | Original/listed product price                                   |
| `is_best_seller`           | Indicates whether the product has a Best Seller badge           |
| `is_sponsored`             | Indicates whether the listing is sponsored                      |
| `is_couponed`              | Indicates whether a coupon is available                         |
| `buy_box_availability`     | Product Buy Box availability                                    |
| `delivery_details`         | Product delivery information                                    |
| `sustainability_badges`    | Sustainability-related product badge                            |
| `image_url`                | Product image URL                                               |
| `product_url`              | Product listing URL                                             |
| `collected_at`             | Dataset collection timestamp                                    |

The raw dataset initially stored all 16 columns as object/string-like data, making data-type validation an important part of the cleaning process.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook**

---

## 🔄 Data Cleaning Workflow

```text
Raw Amazon Dataset
        ↓
Dataset Loading
        ↓
Initial Inspection
        ↓
Data Quality Assessment
        ↓
Duplicate Detection
        ↓
Missing Value Analysis
        ↓
Column Name Standardization
        ↓
Text Standardization
        ↓
Data Type Conversion
        ↓
Missing Value Treatment
        ↓
Outlier Detection
        ↓
IQR-Based Outlier Capping
        ↓
Duplicate Removal
        ↓
Before vs After Quality Comparison
        ↓
Exploratory Data Analysis
        ↓
Insights
        ↓
Cleaned Dataset
```

---

## 🧹 Data Cleaning Performed

### 1. Initial Data Inspection

The dataset was loaded using Pandas and examined using:

* `head()`
* `shape`
* `info()`
* `describe()`

The initial dataset contained **8,127 records and 16 columns**.

---

### 2. Data Quality Assessment

A data-quality report was created containing:

* Column names
* Data types
* Missing-value counts
* Missing-value percentages
* Number of unique values

This provided a baseline for evaluating the quality of the dataset before cleaning.

---

### 3. Duplicate Detection

The dataset contained **272 duplicate rows**.

Duplicate records were identified before cleaning and subsequently removed from the final dataset.

---

### 4. Missing Value Analysis

Missing values were identified across several fields.

The major missing-value counts included:

| Column                     | Missing Values |
| -------------------------- | -------------: |
| `Rating`                   |             15 |
| `Number_of_reviews`        |             15 |
| `bought_in_last_month`     |            717 |
| `Current/discounted_price` |          2,074 |
| `buy_box_availability`     |          2,510 |
| `delivery_details`         |          2,081 |
| `sustainability_badges`    |          7,217 |
| `product_url`              |            563 |
| `collected_at`             |              1 |

Overall, the raw dataset contained **15,193 missing values**.

---

### 5. Column Name Standardization

Column names were standardized by:

* Removing unnecessary spaces
* Converting names to lowercase
* Replacing spaces with underscores
* Removing unnecessary special characters

For example:

```text
Current/discounted_price
        ↓
current_discounted_price
```

The final standardized column names were generated consistently across the dataset.

---

### 6. Text Standardization

Text-based columns were stripped of unnecessary leading and trailing whitespace.

This helps maintain consistent categorical and textual values throughout the dataset.

---

### 7. Data Type Conversion

The cleaning workflow checked string/object columns and attempted to convert columns containing predominantly numerical values into appropriate numerical data types.

Values containing characters such as:

```text
,
$
%
```

were cleaned before numerical conversion.

---

### 8. Missing Value Treatment

Categorical/string columns were handled using the **mode** where an appropriate value was available.

Numerical columns were handled using **median imputation**, which is less sensitive to extreme values than mean-based imputation.

---

## 📉 Outlier Detection

Numerical outliers were detected using the **Interquartile Range (IQR)** method.

```text
IQR = Q3 - Q1

Lower Bound = Q1 - 1.5 × IQR

Upper Bound = Q3 + 1.5 × IQR
```

The analysis identified `number_of_reviews` as the numerical field requiring outlier analysis.

The calculated IQR boundaries were:

* **Q1:** 180
* **Q3:** 5,061
* **Lower Bound:** -7,141.5
* **Upper Bound:** 12,382.5
* **Detected outliers:** 838

---

## ✂️ Outlier Treatment

Instead of deleting rows containing extreme values, the project used **IQR-based capping**.

Values outside the calculated lower and upper boundaries were capped at those boundaries.

This approach preserves the observations while reducing the influence of extreme values on numerical analysis.

---

## 🗑️ Duplicate Removal

After the cleaning process, the 272 duplicate records were removed.

### Dataset size:

```text
Before Cleaning : 8,127 rows
After Cleaning  : 7,855 rows
Rows Removed    : 272
```

The dataset retained all **16 columns**.

---

## 📊 Before vs After Data Quality

The project compares the dataset before and after cleaning using:

* Number of rows
* Number of columns
* Duplicate records
* Total missing values

### Results

| Metric               | Before Cleaning | After Cleaning |
| -------------------- | --------------: | -------------: |
| Rows                 |           8,127 |          7,855 |
| Columns              |              16 |             16 |
| Duplicate Rows       |             272 |              0 |
| Total Missing Values |          15,193 |              0 |

The final quality report confirms that all remaining columns contain **zero missing values**.

---

## 📈 Exploratory Data Analysis

After cleaning, additional analysis and visualizations were performed.

### 1. Distribution of Number of Reviews

A histogram was created to understand the distribution of product review counts.

### 2. Product Rating Distribution

The rating text was converted into a numerical rating value for analysis.

The extracted ratings ranged from approximately **4.0 to 5.0**, with the analyzed values concentrated in the higher-rating range.

### 3. Rating vs Number of Reviews

A scatter plot was created to examine the relationship between:

* Product rating
* Number of reviews

This provides a visual comparison of product popularity and customer ratings.

### 4. Ratings by Best Seller Status

A box plot was used to compare product ratings between different Best Seller statuses.

### 5. Top Products by Number of Reviews

The project also identifies the **top 10 products by number of reviews**.

The analysis includes product title, review count, and numerical rating.

---

## 🔎 Key Results

The cleaning process produced the following measurable improvements:

* **8,127 → 7,855 rows**
* **272 duplicate rows removed**
* **15,193 → 0 missing values**
* Dataset retained **16 columns**
* Numerical outliers were identified using the IQR method.
* `number_of_reviews` contained **838 observations identified as outliers** before capping.

The cleaned dataset contains **7,855 rows and 16 columns** and was exported as `cleaned_dataset.csv`.

---

## 📁 Project Structure

```text
Level 1 : Task 3 - Cleaning Data/
│
├── Cleaning Data.ipynb
├── Cleaning Data.pdf
├── README.md
└── amazon_sales_data_uncleaned.csv.zip
```

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/Sasikumar021/OIBSIP.git
```

### 2. Navigate to the Project

```text
Data Analytics/
└── Level 1 : Task 3 - Cleaning Data/
```

### 3. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Open Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
Cleaning Data.ipynb
```

### 5. Run the Notebook

Execute the cells sequentially to reproduce the cleaning and exploratory analysis workflow.

---

## 📤 Project Deliverables

| File                                  | Description                                     |
| ------------------------------------- | ----------------------------------------------- |
| `Cleaning Data.ipynb`                 | Complete Python notebook                        |
| `Cleaning Data.pdf`                   | PDF version of the analysis                     |
| `amazon_sales_data_uncleaned.csv.zip` | Raw dataset                                     |
| `README.md`                           | Project documentation                           |
| `cleaned_dataset.csv`                 | Final cleaned dataset generated by the notebook |

---

## 🎓 Skills Demonstrated

### Data Analytics

* Data Cleaning
* Data Preprocessing
* Exploratory Data Analysis
* Data Quality Assessment
* Missing Value Handling
* Duplicate Detection
* Outlier Analysis

### Python

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

### Analytical Techniques

* IQR Outlier Detection
* Median Imputation
* Mode Imputation
* Data Type Conversion
* Categorical Standardization
* Descriptive Statistics
* Correlation Analysis

---

## 👨‍💻 Author

**P. Sasi Kumar**

Aspiring **Data Analyst**

**Technical Skills:**
`Python` · `SQL` · `Pandas` · `NumPy` · `Power BI` · `Excel` · `Matplotlib` · `Seaborn` · `Data Cleaning` · `EDA`

---

## ⭐ Project

This project was completed as part of **Oasis Infobyte Data Analytics – Level 1, Task 3: Cleaning Data**.

The project demonstrates how raw, inconsistent data can be systematically cleaned, validated, analyzed, and prepared for downstream data analytics.

