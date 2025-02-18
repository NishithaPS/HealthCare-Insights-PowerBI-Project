# Healthcare Insights Power BI Dashboard

![Power BI Dashboard](https://your-image-link.com)

## 📌 Overview
This Power BI project provides an in-depth analysis of patient waiting lists using publicly available healthcare data. The dashboard enables stakeholders to track and analyze patient waiting times across different categories, specialties, and age groups. The ultimate goal is to enhance decision-making by providing actionable insights into waiting list trends, key performance indicators (KPIs), and historical data.

---

## 🚀 Project Steps & Implementation

### 1️⃣ Requirement Gathering
**🔹 Problem Statement & Objectives:**
- 📊 Track the current status of the patient waiting list.
- 📅 Analyze historical monthly trends for Inpatient & Outpatient categories.
- 🏥 Conduct a detailed specialty-level and age-profile analysis.
- 🎯 Define KPIs such as average and median waiting list times.
- 📆 Establish deployment timelines and scope (**2018 – 2021**).

---

### 2️⃣ Data Collection
**📡 Data Sources & Connectors:**
- 📂 Excel / CSV files
- 🔗 Folder Connection for automatic updates
- 🛢️ Other potential sources: SQL Server, Cloud Platforms, Web APIs

**📥 Data Import Process:**
- Used the **Folder Connector** in Power BI to load Inpatient and Outpatient data.
- Combined and structured datasets for further analysis.

---

### 3️⃣ Data Transformation & Modelling
**🛠️ Data Cleaning & Transformation Steps:**
- ✅ Renamed columns to maintain consistency (e.g., `Specialty` vs. `Specialty_Name`).
- 🔄 Rearranged columns for uniformity.
- ➕ Created a new **Case_Type** column in Outpatient data.
- 🔗 Appended Inpatient and Outpatient tables into a single **All_Data** table.
- 🧹 Cleaned `Age_Profile` & `Time_Band` values using Replace and Trim functions.

**🔗 Data Modelling:**
- Established relationships between tables using **Specialty Mapping Table**.
- Created **1-to-Many relationships** between Mapping Table and All_Data.

---

### 4️⃣ Visualization Blueprint
- Developed a wireframe layout for approval.
- Structured dashboard pages:
  - 📊 **Summary Page:** Key KPIs and Visuals
  - 📋 **Detailed View:** Matrix for granular analysis
  - 🛠 **Tooltip Page:** Specialty-wise breakdown

---

### 5️⃣ Dashboard Layout & Design
#### 📌 **DAX Measures:**
```DAX
Latest Month Wait List = CALCULATE(SUM(All_Data[Total]), All_Data[Archive_Date] = MAX(All_Data[Archive_Date])) + 0

PY Latest Month Wait List = CALCULATE(SUM(All_Data[Total]), All_Data[Archive_Date] = EDATE(MAX(All_Data[Archive_Date]), -12)) + 0

Median Wait List = MEDIAN(All_Data[Total])

Average Wait List = AVERAGE(All_Data[Total])

Avg/Med Wait List = SWITCH(VALUES('Calculation Method'[Calc Method]), "Average", [Average Wait List], "Median", [Median Wait List])

Dynamic Title = SWITCH(VALUES('Calculation Method'[Calc Method]), "Average", "Key Indicators - Patient Wait List (Average)", "Median", "Key Indicators - Patient Wait List (Median)")

NoDataLeft = IF(ISBLANK(CALCULATE(SUM(All_Data[Total]), All_Data[Case_Type] <> "Outpatient")), "No data for selected criteria", "")

NoDataRight = IF(ISBLANK(CALCULATE(SUM(All_Data[Total]), All_Data[Case_Type] = "Outpatient")), "No data for selected criteria", "")
```

#### 📊 **Dashboard Elements:**
- **KPIs & Summary Cards**: Display total wait list, median wait time, etc.
- **Visuals:**
  - 📉 **Doughnut Chart:** Distribution of waiting list by category.
  - 📊 **Clustered Column Chart:** Monthly trends.
  - 🔝 **Multi-row Cards:** Top 5 specialties with highest waiting times.
  - 📈 **Line Charts:** Trends for Inpatients vs. Outpatients.
- **Filters & Slicers:** Archive_Date, Case_Type, Specialty.
- **Dynamic Tooltips:** Specialty breakdown on hover.
- **Interactive Slicer:** Toggle between **Average & Median Wait List**.

---

### 6️⃣ Adding Interactivity
- 🖱 **Navigation Buttons** for seamless page transitions.
- 🏷 **Hover Tooltips** for deeper insights.

---

### 7️⃣ Testing & Sharing
- ✅ Conducted **User Acceptance Testing (UAT)** to validate data accuracy.
- 🔒 Implemented **Row Level Security (RLS)** for role-based access.
- 🌐 Published dashboard in Power BI Service for stakeholder access.

---

### 8️⃣ Routine Refresh & Maintenance
- 🔄 **Automated Data Refresh:** Configured via Power BI Service.
- 📊 **Data Quality Checks:** Routine audits for missing values and anomalies.

---

## 📈 Key Insights

### 🔹 1. **Current Patient Waiting List Status**
- **Total Patients:** X
- **Monthly Change:** 📈 **Y% Increase** / 📉 **Y% Decrease**
- **Breakdown by Type:**
  - 🏥 **Inpatients:** X patients (**Y% of total**)
  - 🚑 **Outpatients:** X patients (**Y% of total**)

### 🔹 2. **Historical Trends (2018-2021)**
- 📉 **Annual Growth Rate:** X%
- 📅 **Seasonal Trends:** Highest patient influx in **Month/Quarter**.
- 🦠 **COVID-19 Impact:** Major fluctuations observed in **2020-2021**.

### 🔹 3. **Specialty-Wise Analysis**
- **Top 5 Specialties with Highest Waiting List**
  1. 🏥 Specialty A - X patients
  2. 🏥 Specialty B - X patients
  3. 🏥 Specialty C - X patients
  4. 🏥 Specialty D - X patients
  5. 🏥 Specialty E - X patients

### 🔹 4. **Age Profile Analysis**
- **Elderly (65+) patients** have the highest waiting times.
- 📉 Young patients (0-18) have the lowest wait times.

### 🔹 5. **Comparative Performance Metrics**
- **Hospital A vs. Hospital B:** Differences in waiting times.
- 📉 Policy changes led to a **X% reduction** in waiting times.

---

## 🎯 Recommendations & Future Enhancements
- **🔍 Optimize Resource Allocation**
- **📉 Reduce Long-Term Waiting Cases**
- **📊 Improve Data Quality & Monitoring**
- **📈 Policy & Strategic Adjustments**
- **🤖 AI-Based Predictions & Machine Learning Enhancements**

---

## 🎯 Conclusion
This Power BI dashboard provides valuable insights into patient waiting times and healthcare service efficiency. By leveraging these insights, stakeholders can make data-driven decisions to enhance healthcare accessibility and efficiency. Future improvements in predictive analytics and automation will further refine this analysis for better healthcare planning.

🚀 **Happy Analyzing!** 🏥📊

