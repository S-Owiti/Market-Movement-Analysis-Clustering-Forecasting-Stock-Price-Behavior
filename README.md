**Project Title**: *Market Movement Analysis: Clustering & Forecasting Stock Price Behavior*
**Dataset Chosen**: Stock Prices Dataset
**Total Rows**: 497,472
**Total Columns**: 7
**File Type**: `.csv`

---

### 🔍 Why This Dataset?

The selected dataset contains **time-stamped stock data** with fields including:
`symbol`, `date`, `open`, `high`, `low`, `close`, `volume`.

This dataset is ideal for:

* **Clustering stocks** by behavior (volatility, movement)
* **Time series forecasting** using price trends
* Demonstrating **real-world business insight** for investment strategy and market movement prediction

---

### 🧱 Project Blueprint

**Data Workflow Layers:**

1. **Foundation Layer – Data Handling**
   Data cleaning, type validation, missing value imputation, anomaly checks
2. **Core Analysis Layer – Modelling Brain**
   Clustering + Time Series Forecasting
3. **Advanced Analytics Layer – Insight & Differentiation**
   Volatility trends, return analysis, strategic interpretation

---

### 🧼 Preprocessing Steps

#### 1. **Data Type Conversion**

* Converted `date` to `datetime64` to enable accurate time-based grouping and calculations.

#### 2. **Missing Values**

* **27 missing values** identified across `open`, `high`, and `low`.
* Imputed or dropped depending on context.

#### 3. **Duplicates**

* Checked: ✅ **0 duplicates found**.

#### 4. **Price Consistency Validation**

* Ensured that each row met the rule:
  `low ≤ close ≤ high`
* **9 rows eliminated** for violating this rule.

```python
df = df[(df['low'] <= df['close']) & (df['close'] <= df['high'])]
```

---

### 📊 Feature Engineering

New columns were added to enhance analysis, clustering, and forecasting:

| Feature            | Description                                           |
| ------------------ | ----------------------------------------------------- |
| `z_close`          | Z-score of the closing price, used to detect outliers |
| `MA7`              | 7-day moving average of the `close` price             |
| `Volatility`       | 7-day rolling standard deviation of the `close` price |
| `Return`           | % Change in close price per day (unsmoothed)          |
| `Lag_1_close`      | Previous day’s closing price                          |
| `Lag_7_volume`     | Trading volume from 7 days prior                      |
| `Daily_Return`     | Day-over-day return in decimal                        |
| `Daily_Return (%)` | Day-over-day return expressed as a percentage         |

---

### 🤔 Why Rolling Averages?

* Helps smooth market noise to better spot trends
* Makes visualizations more meaningful
* Essential for comparing **short-term (7-day)** vs **long-term (30-day)** price behavior
* Supports better segmentation and forecasting accuracy

---

### 📈 Initial Data Profile

```text
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 497472 entries, 0 to 497471
Data columns (total 7):
symbol        497472 non-null object
date          497472 non-null object → converted to datetime
open          497461 non-null float64
high          497464 non-null float64
low           497464 non-null float64
close         497472 non-null float64
volume        497472 non-null int64
```

* **Memory usage**: 26.6 MB
* **Cleaned dataset shape**: *(497,463, 15)* after consistency validation

---

### ✅ Summary

The dataset was successfully cleaned and enhanced for modeling.
All major **data integrity checks** (nulls, types, anomalies) have been passed.
Key **statistical features and time-aware fields** are now available for the next steps:
**Exploratory Data Analysis, Clustering, and Time Series Forecasting.**

