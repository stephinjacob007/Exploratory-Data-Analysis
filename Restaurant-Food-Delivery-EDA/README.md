# 🚴‍♂️ Restaurant Food Delivery - Exploratory Data Analysis (EDA)

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Latest-maroon.svg)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-Latest-orange.svg)](https://seaborn.pydata.org/)
[![Kaggle](https://img.shields.io/badge/Kaggle-Dataset-blue)](https://www.kaggle.com/datasets/ankitkalauni/the-food-delivery-time-for-different-cuisines)

An end-to-end Exploratory Data Analysis (EDA) engineered to uncover operational inefficiencies, pricing distribution, rating trends, and delivery-time behaviors across multiple restaurants, major metropolitan hubs, and diverse cuisine pairings. 

The project pipeline is built from scratch in a production-oriented format using a structured Jupyter Notebook (`.ipynb`), strict dependency isolation, data cleaning validation, and an interactive, analytical question-and-answer layout.

---

## 📌 Project Overview & Structure
The workflow follows a rigorous analytical blueprint designed to guarantee high data integrity before visual mapping or descriptive inferences are drawn:

```text
📁 Exploratory-Data-Analysis (Root)
│
├── 📄 Data_Train.xlsx           # Raw input dataset containing 11,094 instances
├── 📓 Food_Delivery_EDA.ipynb  # Main, heavily-commented Jupyter Notebook pipeline
└── 📄 README.md                 # Project documentation & insight summary

```

The notebook architecture is explicitly broken into sequential processing stages:

* **Section 1:** Data Loading & Ecosystem Instantiation
* **Section 2:** Initial Metadata Inspection & Structural Validation
* **Section 3:** Programmatic Data Cleaning & Feature Preprocessing
* **Section 4:** Question-Driven Exploratory Data Analysis & Advanced Visualizations

---

## 🛠️ Technology Stack & Core Dependencies

To maintain lightweight execution performance and standard scientific compute dependencies, the engine relies strictly on:

* **Core Computational Logic:** `NumPy` & `Pandas`
* **Static Visual Analytics Layer:** `Matplotlib.pyplot` & `Seaborn`
* **File Processing System:** `Openpyxl` (Engine dependency for loading localized `.xlsx` formats)

---

## 🧼 Programmatic Data Cleaning & Transformation Pipeline

The raw dataset was uniformly loaded with all features formatted as generic `object` (string) datatypes, compounded by unstandardized strings, currency markers, non-numeric placeholders, and implicit omissions. The cleaning engine engineered the following modifications natively:

1. **Duplicate Mitigation:** Verified individual records and systematically purged duplicate elements to prevent statistical skewing.
2. **`Average_Cost` Standardization:** Extracted currency symbols (`₹`) and string comma separators. Found and isolated anomalous structural values (such as `'for'`), coercing them to `NaN`, and imputed missing elements dynamically using the historical distribution's `median`.
3. **`Minimum_Order` Type Casting:** Stripped string artifacts and currency parameters (`₹`), standardizing the array into robust numerical `int` variables.
4. **`Rating` Array Normalization:** Evaluated qualitative status records (`'NEW'`, `'Opening Soon'`, `'Temporarily Closed'`, and missing labels `'-'`), programmatically mapped them to a null index (`NaN`), and recast features to high-precision `float64`.
5. **Operational Volume Rectification (`Votes` & `Reviews`):** Evaluated null indicators (`'-'`) across interactive features, initialized them to `0` (denoting unrecorded user history or a nascent restaurant lifecycle), and parsed variables into true `int32` arrays.
6. **`Delivery_Time` Parsing:** Isolated and purged the descriptive suffix text string (`' minutes'`) to generate numerical vectors representing exact duration runtimes.
7. **Feature Engineering (City Extraction & Variety Profiling):**
* Generated an optimized string parsing function (`get_city`) to abstract structural metadata from the alphanumeric `Location` row, successfully mapping entities across primary urban metrics: **Pune, Delhi, Kolkata, Hyderabad, Noida, Mumbai, Gurgaon, and Bangalore**.
* Evaluated string delimiters (`','`) within the `Cuisines` field to compute a scalar parameter called `Cuisine_Count`.



---

## 📊 Question-Driven Visualizations & Extracted Insights

### Q1: What is the distribution of Delivery Time across the restaurants?

* **Analytical Vector:** Distribution Analysis (`sns.countplot`)
* **Core Insight:** The local logistics network showcases a highly tiered delivery schedule. Roughly **66.7%** of all historical delivery tasks are strictly completed within a **30-minute** flat threshold. Extreme delays exceeding 65 minutes are isolated exceptions, pointing to optimized short-distance dispatching but structured batch scheduling in back-end hubs.

### Q2: Is there a correlation between the metrics (Average_Cost, Minimum_Order, Rating, Votes, Reviews, Cuisine_Count, Delivery_Time)?

* **Analytical Vector:** Multivariate Interaction Matrix (`sns.heatmap` with correlation coefficients)
* **Core Insight:** A definitive operational correlation (**~0.96**) exists between a restaurant's aggregate user interaction metrics (`Votes` and `Reviews`). More importantly, a subtle upward correlation exists between `Cuisine_Count` and pricing, proving that complex, multi-variety menus allow restaurants to charge higher average ticket counts.

### Q3: How does the Average Cost vary across different Cities?

* **Analytical Vector:** Cross-Geographic Stratification (`sns.boxplot` on log-transformed scales or filtered price medians)
* **Core Insight:** Operational baselines show pricing consistency across standard urban regions. However, Tier-1 economic centers such as **Mumbai** and **Bangalore** display a higher density of high-end outlier values, confirming concentrated luxury demand in tech corridors and financial hubs compared to institutional sectors like Delhi University.

### Q4: Does a higher Rating lead to a higher Average Cost or Minimum Order?

* **Analytical Vector:** Relational Trend Mapping (`sns.scatterplot` and `sns.lmplot`)
* **Core Insight:** Premium user sentiment is concentrated within top pricing tiers. Elite restaurants (Ratings $\ge$ 4.5) systematically enforce elevated barrier limits with high `Minimum_Order` rules. Conversely, low-tier value restaurants are highly concentrated within lower satisfaction boundaries, showing that pricing constraints directly impact food quality or service speed.

### Q5: How does Delivery Time vary for the Top 5 Cuisines?

* **Analytical Vector:** Categorical Variance Profiling (`sns.boxplot` utilizing string explosions for top keys)
* **Core Insight:** Evaluating the top 5 localized demand matrices (**North Indian, Fast Food, Chinese, Mughlai, and Beverages**) indicates that logistical runtimes are highly standardized across core groups. The median processing window hovers perfectly around **30 minutes**, proving kitchen automation and high ingredient availability for these staple items across cloud-kitchen layouts.

---

## 🚀 How to Execute the Notebook Locally

1. **Clone the Repository:**
```bash
git clone [https://github.com/stephinjacob007/Exploratory-Data-Analysis/Restaurant-Food-Delivery-EDA.git]((https://github.com/stephinjacob007/Exploratory-Data-Analysis/Restaurant-Food-Delivery-EDA.git))
cd Exploratory-Data-Analysis
cd Restaurant-Food-Delivery-EDA

```


2. **Establish Environment Dependencies:**
Ensure your Python runtime environment has the necessary processing packages installed:
```bash
pip install numpy pandas matplotlib seaborn openpyxl notebook

```


3. **Launch the Engine:**
```bash
jupyter notebook Food_Delivery_EDA.ipynb

```



---

## 🎯 Key Takeaways for Business Strategy

* **Logistical Standardization:** Since most orders are resolved within 30 minutes, logistics algorithms should focus heavily on the subset of orders that spill over to the 45-65 minute mark to find dispatch blockages.
* **Menu Engineering Optimization:** Restaurants providing a high configuration of items (`Cuisine_Count`) drive higher target basket metrics (`Average_Cost`) without adding clear delays to delivery operations. This justifies an increase in multi-brand cloud kitchen concepts.
