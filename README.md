# 🌍 Air Quality Data Pipeline on Snowflake

## 🧭 Project Overview
This project implements an **end-to-end data pipeline architecture** using **Snowflake (on AWS)** to collect, process, and visualize **Air Quality Index (AQI)** data from multiple global monitoring stations.  
It automates hourly data extraction, performs data cleansing and modeling, and publishes real-time dashboards for analysis and decision-making.

---

## 🎯 Mission Statement
To build a centralized data platform that aggregates global Air Quality Index (AQI) data from multiple monitoring stations and supports an interactive dashboard, allowing users to explore both real-time and historical air quality and pollutant levels with ease.

### 🏆 Goal / Business Value
This solution empowers environmental analysts, policymakers, and the public to make **data-driven decisions** by providing accurate, time-based insights into air quality trends and pollution patterns worldwide.

---

## 🧱 End-to-End Data Flow Architecture

### 1️⃣ Data Source Layer
- **Inputs:** Air Quality data from public HTTP APIs and marketplace shared databases.  
- **Automation:** Hourly **GitHub Actions** trigger data extraction workflows.  
- **Process:**
  - APIs return AQI and pollutant data in **JSON** format.  
  - Data is stored in **GitHub** for version control and auditability.

### 2️⃣ Stage Layer
- **Purpose:** Securely ingest and store raw JSON data in Snowflake.  
- **Process:**
  - Data from GitHub and marketplace databases is loaded into the **Landing Layer** using **LOAD_WH** warehouse.
  - Raw JSON files are preserved for audit and schema evolution.

### 3️⃣ Clean Layer
- **Purpose:** Flatten, cleanse, and standardize data.  
- **Process:**
  - Parse and flatten JSON into structured tables using Snowflake SQL.  
  - Apply validation, null handling, and type consistency checks.  
  - Store results as **Flatten Tables**.

### 4️⃣ Consumption Layer
- **Purpose:** Organize data for analytics and visualization.  
- **Process:**
  - Use **Snowflake SQL transformations** to create **fact and dimension models**.  
  - Transformations run in **TRANSFORM_WH** warehouse.  
  - Enables trend analysis and city-wise AQI comparison.

### 5️⃣ Publish Layer
- **Purpose:** Deliver analytical insights to users.  
- **Process:**
  - Publish modeled data to **Streamlit** dashboards via **STREAMLIT_WH** warehouse.  
  - Visualize historical trends, city comparisons, and pollutant breakdowns.

### 6️⃣ End Users
- **Audience:** Analysts, policymakers, and general users.  
- **Access:** Interactive **Streamlit dashboard** to explore AQI and pollutant data over time.

---

## 🧩 Architecture Summary

| **Layer** | **Purpose** | **Warehouse** | **Output** |
|------------|--------------|----------------|-------------|
| Data Source | Extract data from APIs & marketplace | — | JSON Files |
| Stage | Store raw data | `LOAD_WH` | Landing Layer |
| Clean | Flatten & cleanse data | `LOAD_WH` | Flatten Tables |
| Consumption | Model & integrate data | `TRANSFORM_WH` | Dimensional Tables |
| Publish | Visualize & publish analytics | `STREAMLIT_WH` | Streamlit Dashboard |

---

## ⚙️ Technology Stack
- **Cloud Data Platform:** Snowflake (AWS)
- **Programming Language:** Python
- **Workflow Automation:** GitHub Actions
- **Data Orchestration:** Airflow / Cron
- **Data Transformation:** Snowflake SQL, Snowpark, Pandas
- **Visualization:** Streamlit / Power BI / Tableau
- **Version Control:** GitHub
- **CI/CD Integration:** GitHub Actions

---

## 🚀 Key Features
- 🔁 **Automated hourly data ingestion** using GitHub Actions.  
- 🧹 **Data quality checks and schema evolution** supported via Snowflake.  
- 📊 **Historical and predictive analytics** using time-series modeling.  
- ⚡ **Multi-layer Snowflake architecture** for scalability and performance.  
- 🌐 **Interactive dashboards** for real-time insight visualization.

---

## 📈 Project Tagline
> “Turning global air data into actionable insights.”

---

## 🧠 Author
**Nelson Ukaegbu**  
_Data Engineer | Cloud Data Enthusiast | Snowflake Developer_

📧 Contact: [LinkedIn Profile](https://www.linkedin.com/) | [GitHub](https://github.com/nelson-analytics)

