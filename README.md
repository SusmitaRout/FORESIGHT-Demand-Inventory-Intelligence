# FORESIGHT – Demand & Inventory Intelligence

## 📌 Project Overview

FORESIGHT is a demand forecasting and inventory intelligence solution designed to help a direct-to-consumer home and lifestyle business make better inventory planning decisions.

The system uses historical sales, product, calendar, pricing, promotion, and inventory-related information to forecast weekly SKU-level demand and identify products that may require inventory action.

The objective is to help the business:

* Reduce stockout risk for high-demand products
* Identify overstock and slow-moving inventory
* Detect dead-stock products
* Improve inventory planning using data-driven forecasts
* Support better reorder, clear, or leave decisions

---

## 🎯 Business Problem

The business currently relies heavily on spreadsheets and manual judgement for inventory planning.

This can result in:

* Best-selling products going out of stock
* Excess inventory accumulating for slow-moving products
* Dead stock occupying warehouse space
* Missed sales opportunities
* Difficulty identifying inventory risks early

FORESIGHT addresses this problem by combining **demand forecasting** with **inventory risk analysis**.

---

## 📊 Dataset

The project uses SKU-level sales, product, calendar, pricing, promotion, and inventory information.

### Key data sources

* **Sales data** – daily SKU-level units sold and revenue
* **SKU master data** – product category, subcategory, cost, price, launch information, and lead time
* **Calendar data** – date, week, month, quarter, season, holidays, and promotion events
* **Inventory snapshots** – inventory information used for inventory analysis

### Main features

Examples of features used in the analysis include:

* SKU
* Date
* Units sold
* Revenue
* Unit price
* Promotion flag
* Year
* Month
* Week
* Day of week
* Quarter
* Weekend flag
* Season
* Holiday flag
* Promotion event
* Category
* Subcategory
* Launch date
* Unit cost
* List price
* Lead time

---

## 🔍 Data Quality & EDA

The data was profiled and cleaned before modeling.

Key data preparation activities included:

* Checking missing values
* Checking duplicate records
* Validating data types
* Handling missing promotion-event values
* Checking SKU and date consistency
* Creating calendar-based features
* Aggregating daily sales into weekly SKU-level sales
* Identifying slow-moving and dead-stock products

### Key EDA findings

The analysis identified:

* **13 dead-stock SKUs**
* **7 slow-moving SKUs**
* Significant differences in demand across SKUs
* Seasonal variation in demand
* Differences in sales performance during promotional periods

The highest-selling SKUs included:

| SKU     | Units Sold |
| ------- | ---------: |
| SKU0182 |    134,753 |
| SKU0039 |    117,398 |
| SKU0169 |    103,352 |
| SKU0018 |    102,615 |
| SKU0031 |    101,984 |

---

## 📈 Demand Forecasting

The forecasting workflow operates at the **weekly SKU level**.

A **Seasonal Naive** model was used as the baseline.

The baseline provides a simple benchmark against which the machine-learning model can be evaluated.

The main machine-learning model used was:

### Random Forest

The Random Forest model was trained using historical demand and engineered features to predict future weekly demand.

---

## 🧪 Train-Test Split

A time-based split was used to prevent future information from leaking into the training data.

### Training period

**2022-01-02 to 2025-07-06**

### Testing period

**2025-07-13 to 2026-01-04**

Dataset shapes:

```text
Training data: 36,800 rows
Testing data:   5,200 rows
```

The modeling workflow can be found in:

`notebooks/05_demand_forecasting.ipynb`

---

## 📏 Model Evaluation

The model was evaluated using **WAPE (Weighted Absolute Percentage Error)**.

### Results

| Model                   |       WAPE |
| ----------------------- | ---------: |
| Seasonal Naive Baseline | **11.65%** |
| Random Forest           | **10.30%** |

The Random Forest model reduced WAPE from **11.65% to 10.30%**, representing an improvement over the baseline.

This indicates that the machine-learning model provides more accurate demand forecasts than the selected seasonal-naive benchmark on the test period.

---

## 📦 Inventory Risk Analysis

FORESIGHT combines demand forecasting with inventory analysis to support inventory decisions.

The system can help identify:

### 🔴 Stockout Risk

Products that may run out of inventory based on expected future demand and available stock.

### 🟠 Overstock Risk

Products where inventory levels may be significantly higher than expected demand.

### 🟡 Slow-Moving Inventory

Products with relatively low sales velocity.

### ⚫ Dead Stock

Products with little or no recent demand that may require clearance or other action.

These insights help transform forecasting results into actionable inventory decisions.

---

## 📊 Power BI Dashboard

The project includes an interactive Power BI dashboard designed for business users.

The dashboard provides visibility into:

* Overall sales performance
* SKU demand
* Top-performing products
* Seasonal demand
* Promotion impact
* Inventory risk
* Dead-stock and slow-moving SKUs
* Forecast/model performance



---

## 🚀 Project Structure

```text
FORESIGHT-Demand-Inventory-Intelligence/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── models/
│   └── trained model files
│
├── notebooks/
│   ├── 02_data_profiling.ipynb
    ├── 03_data_cleaning.ipynb
    ├── 04_data_analysis.ipynb
│   └── 05_demand_forecasting.ipynb
│
├── outputs/
│   └── analysis and model outputs
│
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

## ⚙️ Setup & Installation

### 1. Clone the repository

```bash
git clone https://github.com/SusmitaRout/FORESIGHT-Demand-Inventory-Intelligence.git
```

### 2. Navigate to the project

```bash
cd FORESIGHT-Demand-Inventory-Intelligence
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the environment

#### Windows

```bash
venv\Scripts\activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```
---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Matplotlib**
* **Power BI**
* **Git & GitHub**

---

## 📌 Key Assumptions

The project uses the following assumptions:

1. Historical sales patterns provide useful information about future demand.
2. Weekly aggregation is appropriate for inventory planning.
3. The Seasonal Naive model provides a reasonable baseline for comparison.
4. The time-based train-test split represents a realistic forecasting scenario.
5. Historical promotions and calendar features can help explain demand variation.
6. The Random Forest model is evaluated only on the held-out test period.
7. Forecast accuracy is measured using WAPE.
8. Inventory decisions should consider both forecasted demand and current inventory conditions.
9. Model predictions should support business decisions rather than completely replace business judgement.

---

## 📈 Business Impact

FORESIGHT is designed to help inventory teams move from reactive inventory management toward proactive, data-driven planning.

Potential business benefits include:

* Fewer stockout situations
* Better replenishment planning
* Reduced excess inventory
* Earlier identification of slow-moving products
* Better visibility into SKU-level demand
* Improved inventory decision-making

---

## 🔗 Project Links

| Resource           | Link                                                                   |
| ------------------ | ---------------------------------------------------------------------- |
| GitHub Repository  | https://github.com/SusmitaRout/FORESIGHT-Demand-Inventory-Intelligence |

---

FORESIGHT – Demand & Inventory Intelligence

