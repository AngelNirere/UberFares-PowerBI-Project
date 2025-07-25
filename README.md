# 🚗 Uber Fares Dataset Analysis - README

**Course:** Introduction to Big Data Analytics - INSY 8413
**Instructor:** Eric Maniraguha | [eric.maniraguha@auca.ac.rw](mailto:eric.maniraguha@auca.ac.rw)
**Assignment Date:** July 20, 2025
**Deadline:** Friday before Sabbath begins
**Groups:** A, B & E
**Tool:** Python (Jupyter Notebook) + Power BI Desktop
**Dataset:** Uber Fares Dataset (from Kaggle)

---

## 🌟 Project Objective

To perform end-to-end data analysis on Uber fare records using Python and Power BI. The project uncovers patterns in ride fares, durations, geography, and time to gain insights into Uber operations.

---

## 📅 1. Data Understanding & Preparation

### 📂 File Used:

* `uber-raw-data.csv` (Kaggle original)

### 🔧 Steps Taken:

* Loaded the dataset using Pandas in Jupyter Notebook.
* Examined structure: rows, columns, data types.
* Checked for missing values and outliers.
* Cleaned records with nulls, duplicates, or invalid coordinates.
* Parsed timestamps and ensured datetime consistency.
* Saved cleaned version as `uber-cleaned.csv`

### ✅ Output:

Cleaned dataset: `uber-cleaned-with-duration.csv`

---

## 🧰 2. Exploratory Data Analysis (EDA)

Performed with Python:

### ⚖️ Descriptive Statistics:

* Mean, median, mode of fare\_amount
* Standard deviation, quartiles
* Min-max range
* Count of unique passengers

### 📊 Visualizations:

* Histogram: Fare distribution
* Box Plot: Fare amount (outliers)
* Correlation heatmap: Distance, fare, time

### 🌄 Relationships:

* Fare vs Distance: Positive correlation
* Fare vs Hour of Day: Higher in evenings
* Outliers found in high fare or low-distance trips

### 🔢 Key Calculated Fields:

* `trip_distance` (estimated using coordinates)
* `ride_duration_minutes = (trip_distance / 20) * 60`
* Hour, Day, Month, Day\_of\_Week from pickup time

---

## 🌐 3. Feature Engineering

### 🔄 Extracted Fields:

* `hour`, `day`, `month` from timestamp
* `day_of_week` (0 = Monday)
* `ride_duration_minutes` (based on distance)

### 🔄 Encoded Categorical Fields:

* Converted pickup hour to label (morning, evening, etc.)
* Converted day\_of\_week to labels (Monday, etc.)

---

## 📊 4. Data Analysis in Power BI

### 📂 Imported File:

* `uber-cleaned-with-duration.csv`

### 🖊️ Visualizations:

| Visualization                | Description                      | Status |
| ---------------------------- | -------------------------------- | ------ |
| Histogram of fare\_amount    | Distribution of fares            | ✅ Done |
| Box plot of fare\_amount     | Outlier detection                | ✅ Done |
| Ride duration (time-based)   | Based on `ride_duration_minutes` | ✅ Done |
| Time series trend            | `pickup_datetime` vs fare        | ✅ Done |
| Geographic map               | Pickup coordinates               | ✅ Done |
| Ride by hour                 | Fare count by hour               | ✅ Done |
| Average fare by weekday      | Bar chart                        | ✅ Done |
| Passenger count distribution | Pie / bar chart                  | ✅ Done |
| Filters: Date/Hour           | Interactivity                    | ✅ Done |

---

## 🔄 5. Dashboard Development in Power BI

* Designed with consistent colors and formatting.
* Included date slicers, drill-downs.
* Grouped charts by themes: Time, Fare, Location.
* Visuals arranged professionally on one screen.

---

## 📚 6. Report Summary

### 📚 Introduction:

The project focuses on deriving operational and economic insights from Uber trip data to understand fare trends, durations, and peak hours.

### 📐 Methodology:

* Python for cleaning, feature creation, and EDA
* Exported dataset to Power BI for visualization
* Applied DAX formulas for calculated columns

### 🔢 Analysis Highlights:

* Most rides are short (<15 mins)
* Fare amount increases with distance and time
* Most rides occur in evening rush hours (4–8 PM)
* Saturdays have higher average fares

### 📊 Results:

* Clear fare distribution seen in histograms and box plots
* Duration and fare patterns aligned with city traffic flow
* Geographic plots show urban hotspot concentrations

### 📄 Conclusion:

Uber rides show predictable time-based and geographic patterns. Strategic pricing and resource allocation can improve profitability.

### 🔹 Recommendations:

* Offer discounts during low-demand hours
* Allocate more drivers to evening rush hours
* Use trip duration models to optimize pricing

---

## 📦 Project Folder Structure

```bash
Uber-Fare-Analysis/
├── README.md
├── cleaned_data/
│   └── uber-cleaned-with-duration.csv
├── notebooks/
│   └── Uber_EDA.ipynb
├── powerbi/
│   └── UberFareDashboard.pbix
├── screenshots/
│   ├── eda_fare_histogram.png
│   ├── duration_analysis.png
│   └── dashboard_view.png
```

---

## 📢 Submission Checklist

* [x] Cleaned CSV uploaded
* [x] Power BI dashboard file
* [x] Jupyter Notebook EDA
* [x] README (this file)
* [x] Report (in markdown / ppt)

---

## 🚀 Tools Used

* Python 3.x (Jupyter Notebook)
* Pandas, Matplotlib, Seaborn
* Power BI Desktop
* GitHub (for collaboration)

---

## 🚀 Live Preview

Power BI file: [UberFareDashboard.pbix](./powerbi/UberFareDashboard.pbix)
Dataset: [uber-cleaned-with-duration.csv](./cleaned_data/uber-cleaned-with-duration.csv)

---

> ✨ "Data is the new oil. But it's crude without analysis!" ✨

Made with ❤️ by Group A, B & E
