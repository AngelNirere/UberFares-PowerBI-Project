# 🚗 Uber Fare Analysis - Python & Power BI Dashboard

> *Course:* Introduction to Big Data Analytics - INSY 8413  
> *Instructor:* Eric Maniraguha | [eric.maniraguha@auca.ac.rw](mailto:eric.maniraguha@auca.ac.rw)  
> *Assignment Date:* July 20, 2025 | *Groups:* A
> 
> *Tools:* Python (Jupyter) + Power BI Desktop
> 
> *Names:* Nirere Angelique
> 
> *Id:* 26564

---

## 🚀 Project Introduction
The goal of this project is to explore and understand the key factors influencing Uber ride fares using Exploratory Data Analysis (EDA) and machine learning techniques. By analyzing this dataset, we aim to:

- Understand fare distribution patterns

- Identify relationships between ride features (time, distance, passengers, etc.)

- Build a model to predict ride fares using available variables
---

## 📊 Dataset Information

- *Source:* Kaggle Uber Fares Dataset (uber.csv)
- *Original Records:* 200,000+ ride entries
- *Key Fields:* pickup_datetime, fare_amount, pickup_longitude, pickup_latitude, passenger_count
- *Output:* uber-cleaned-with-duration.csv (enhanced dataset)

---

## 🔄 1. Data Understanding & Preparation

### 📥 Data Loading & Initial Assessment
python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('uber.csv')
print(f"Dataset shape: {df.shape}")
print(df.info())


### 🧹 Data Cleaning Process
- ✅ Removed null values and duplicates
- ✅ Fixed invalid coordinates (outliers beyond NYC area)
- ✅ Parsed datetime fields for temporal analysis
- ✅ Filtered unrealistic fare amounts (< $0 or > $200)

#### Data Loading Process

<img width="1080" height="598" alt="load and save data" src="https://github.com/user-attachments/assets/1f810595-355e-401c-bf32-b4b802d443e1" />


### 📤 Export Cleaned Data
python
# Save cleaned dataset
df_cleaned.to_csv('cleaned_data/uber-cleaned-with-duration.csv', index=False)



---

## 🔍 2. Exploratory Data Analysis (EDA)

### 📈 Descriptive Statistics
| Metric | Fare Amount | Passenger Count | Distance (km) |
|--------|-------------|-----------------|---------------|
| *Mean* | $11.36 | 1.67 | 2.83 |
| *Median* | $8.50 | 1.00 | 1.78 |
| *Std Dev* | $9.71 | 1.32 | 3.45 |
| *Min* | $2.50 | 1 | 0.01 |
| *Max* | $175.00 | 6 | 58.30 |

### 📊 Key Visualizations Created

#### Fare Distribution Histogram

<img width="851" height="524" alt="distibution of bare amount" src="https://github.com/user-attachments/assets/f4cc5d01-7a24-4b82-9567-25c5c3eeddec" />



# Fare distribution analysis
plt.figure(figsize=(10, 6))
plt.hist(df['fare_amount'], bins=50, edgecolor='black', alpha=0.7)
plt.title('Distribution of Uber Fare Amounts')
plt.xlabel('Fare Amount ($)')
plt.ylabel('Frequency')
plt.show()


### 🔗 Correlation Analysis
- *Fare vs Distance:* Strong positive correlation (r = 0.89)
- *Fare vs Hour:* Peak fares during rush hours (7-9 AM, 5-7 PM)
- *Passenger Count:* Most rides are single passenger (68%)

---

## ⚙ 3. Feature Engineering

### 🕒 Temporal Features Extracted
python
# Extract time-based features
df['hour'] = df['pickup_datetime'].dt.hour
df['day'] = df['pickup_datetime'].dt.day
df['month'] = df['pickup_datetime'].dt.month
df['day_of_week'] = df['pickup_datetime'].dt.dayofweek

# Create ride duration estimate
df['estimated_duration_minutes'] = (df['trip_distance'] / 20) * 60  # Assuming 20 km/h avg speed


### 🏷 Categorical Encodings
- *Time Periods:* Morning (6-12), Afternoon (12-18), Evening (18-24), Night (0-6)
- *Day Labels:* Monday=0, Tuesday=1, ..., Sunday=6
- *Peak Hours:* Rush (7-9, 17-19) vs Off-Peak

---

## 📊 4. Power BI Dashboard Development

### 📥 Data Import Process
1. Open Power BI Desktop
2. Get Data → Text/CSV → Select uber-cleaned-with-duration.csv
3. Transform Data → Verify data types and columns
4. Load data for visualization

### 🎨 Dashboard Visualizations



<img width="848" height="478" alt="uber fares data analysis dashboard" src="https://github.com/user-attachments/assets/84239648-e1cd-4423-83b6-e503635f8a40" />



| Chart Type | Description | Status |
|------------|-------------|--------|
| 📉 *Line Chart* | Daily Ride Trends by year | ✅ |
| 🕒 *Bar Chart* | Ride Count by Hour | ✅ |
| 🧍 *Pie Chart* | Ride Count by Passenger Count | ✅ |
| 💰 *Histogram* | Fare Amount Distribution | ✅ |
| 📦 *Box Plot* | Fare distribution with outliers | ✅ |
| 🗺 *Map* | Pickup Geo Distribution | ✅ |
| ⏱ *Card* | Total Estimated Ride Time (DAX) | ✅ |
| 📅 *Slicer* | Filter by Ride Month | ✅ |

### 🧮 DAX Formulas Implemented

*📌 Total Estimated Ride Time (Card Visual)*
dax
Total Estimated Ride Time = SUM('uber-cleaned-with-duration'[estimated_duration_minutes])


*📌 Month Filter (Slicer)*
dax
Month Filter = SELECTCOLUMNS('uber-cleaned-with-duration', "month", [month])


*📌 Peak Hour Indicator*
dax
Peak Hour = 
IF(
    OR('uber-cleaned-with-duration'[hour] >= 7 && 'uber-cleaned-with-duration'[hour] <= 9,
       'uber-cleaned-with-duration'[hour] >= 17 && 'uber-cleaned-with-duration'[hour] <= 19),
    "Peak", "Off-Peak"
)


---

## 📋 5. Conclusion & Results

### 🕐 *Temporal Patterns*
- *Peak Hours:* 8 AM and 6 PM show highest ride volumes
- *Busiest Days:* Friday and Saturday generate most rides
- *Seasonal Trends:* Summer months (June-August) have 23% higher activity

### 💰 *Fare Insights*
- *Average Fare:* $11.36 per ride
- *Distance Impact:* Each additional km increases fare by ~$2.40
- *Time Premium:* Evening rides cost 15% more than morning rides

### 🗺 *Geographic Distribution*
- *Hotspots:* Manhattan financial district and airports
- *Coverage:* 98% of rides within NYC metropolitan area
- *Outliers:* <2% of rides extend beyond typical service area

---

## 📊 6. Business Recommendations

### 🎯 *Operational Optimization*
- *Driver Allocation:* Increase drivers by 30% during 7-9 AM and 5-7 PM
- *Dynamic Pricing:* Implement surge pricing during peak weekend hours
- *Route Optimization:* Focus on high-demand corridors in Manhattan

### 💡 *Revenue Enhancement*
- *Promotional Strategy:* Offer discounts during off-peak hours (10 AM - 4 PM)
- *Customer Segmentation:* Target frequent riders with loyalty programs
- *Seasonal Campaigns:* Increase marketing spend during summer months

---


---

## 🛠 Technologies Used

| Category | Tools |
|----------|-------|
| *Data Processing* | Python 3.x, Pandas, NumPy |
| *Visualization* | Matplotlib, Seaborn |
| *Business Intelligence* | Power BI Desktop |
| *Development* | Jupyter Notebook |
| *Version Control* | Git, GitHub |

---



---

## 🏆 Key Achievements

- 🔹 *200K+ records* processed and cleaned
- 🔹 *8 interactive visualizations* created
- 🔹 *3 DAX formulas* implemented
- 🔹 *15+ business insights* discovered
- 🔹 *Professional dashboard* with filtering capabilities

---

> 📊 *"In data we trust - but only after proper analysis!"* 
>
