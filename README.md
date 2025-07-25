# 🚗 Uber Fares Dataset Analysis Report

## 🌀 Introduction

The purpose of this project is to analyze the Uber Fares Dataset to uncover meaningful insights that can aid decision-making and performance optimization in ride-hailing services. This report is part of the assignment for the course **Introduction to Big Data Analytics (INSY 8413)**, under the guidance of instructor **Eric Maniraguha**.

## 📊 Methodology

### 📂 Data Collection

The dataset titled **"Uber Ride Price Prediction.csv"** was provided, containing columns like fare\_amount, trip\_distance, pickup and dropoff coordinates, and ride category.

### 📈 Data Cleaning & Preparation

* Removed null/missing values
* Removed outliers based on trip distance and fare amount
* Calculated derived fields like `estimated_duration_minutes`

### 📒 Tools Used

* Python (Pandas, Matplotlib, Seaborn)
* Power BI for interactive visualizations
* Jupyter Notebook for development

## 📅 Analysis

### 1. 👉 Fare Distribution (Histogram)

* **Objective:** Visualize how fare\_amount is distributed.
* **Tool:** Python (Seaborn)
* **Insight:** Majority of fares lie below \$50 with long-tail distribution.

```python
plt.figure(figsize=(10, 5))
sns.histplot(df['fare_amount'], bins=100, kde=True)
plt.title('Fare Amount Distribution 💸')
plt.xlabel('Fare Amount ($)')
plt.ylabel('Frequency')
plt.xlim(0, 100)
plt.show()
```

---

### 2. 🛋️ Trip Distance Distribution

* **Objective:** View the distribution of trip distances
* **Tool:** Histogram
* **Finding:** Most trips are under 20 miles

---

### 3. 🔹 Estimated Duration vs Trip Distance

* **Formula:** `(trip_distance ÷ 20) × 60`
* **Chart:** Scatter Plot
* **Insight:** Linear relation as distance increases

```python
df['estimated_duration_minutes'] = (df['trip_distance'] / 20) * 60
plt.figure(figsize=(10, 5))
sns.scatterplot(data=df, x='trip_distance', y='estimated_duration_minutes', hue='ride_category')
plt.title('Estimated Duration vs Trip Distance ⏳')
plt.xlabel('Trip Distance (miles)')
plt.ylabel('Estimated Duration (minutes)')
plt.show()
```

---

### 4. 📊 Box Plot of Fare Amount

* **Objective:** Show distribution and detect outliers
* **Chart:** Box and Whisker Plot

```python
plt.figure(figsize=(10, 5))
sns.boxplot(x=df['fare_amount'], whis=1.5, color='skyblue')
plt.title('Box Plot of Fare Amount 💸')
plt.xlabel('Fare Amount ($)')
plt.show()
```

---

### 5. 🌐 Geographic Mapping

* **Map:** Power BI
* **Objective:** Visualize pickups and dropoffs using latitude/longitude
* **Insight:** High concentration in urban areas

---

### 6. 🔐 Correlation Heatmap

* **Tool:** Seaborn heatmap
* **Purpose:** Understand relation between fare, distance, duration

```python
corr = df[['fare_amount', 'trip_distance', 'estimated_duration_minutes']].corr()
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.title("Correlation Heatmap 📊")
plt.show()
```

## 📊 Results

* Positive correlation between trip distance and fare
* Duration grows linearly with distance
* Outliers present in fare and distance
* Fare varies with ride category

## 🤝 Recommendations

* 💡 **Outlier Filtering:** Remove extreme fare values to improve ML models
* 🔺 **Surge Pricing:** Adjust pricing based on distance and time
* 🌟 **Route Optimization:** Focus on peak regions visible on map
* ⚙️ **Category Analysis:** Price models should factor in ride\_category

## 🎉 Conclusion

The analysis of Uber fare data provided valuable insights into pricing, trip characteristics, and passenger behavior. Visualizations confirmed expected trends while revealing hidden patterns, such as fare inconsistencies and geographic demand.

> ✨ **Data is not just numbers; it’s a window into real-world behavior.**

---

📗 **Prepared By:** Ishimwe Egîde

📆 **Submission Date:** 25 July 2025
