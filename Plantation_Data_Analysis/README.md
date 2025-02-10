# 🚀 TN Plantation Case Study (2015-2016) – PySpark Analysis  

## 📌 Overview  
This project analyzes the **Area & Production of Plantation Crops by District** in Tamil Nadu for the year **2015-16** using **PySpark**. The goal is to help the Tamil Nadu government generate insights based on the dataset.  

## 🏆 Objectives  
- Identify districts with **maximum and least production** of:  
  - 🍵 Tea  
  - 🎍 Bamboo  
  - 🌳 Rubber  
- Calculate the **total plantation area** per district.  
- Explore relationships between **bamboo, tea, and rubber plantations**.  

## 📊 Dataset  
The dataset is provided inside the folder of this GitHub repository. It is also sourced from the **Tamil Nadu Government's Open Data Portal**:  
🔗 [TN Data Portal](https://tn.data.gov.in/catalog/area-production-productivity-plantation-crops-district-wise-tamil-nadu-year-2015-16)  

### 📝 Schema  
| Column Name      | Data Type | Description |
|-----------------|-----------|-------------|
| Serial_Number   | Integer   | Unique record identifier |
| District        | String    | District name |
| Area           | Integer   | Area under plantation (in hectares) |
| Production     | Integer   | Production quantity |

## ⚙️ Data Preprocessing & Cleaning  
- **Bamboo-plantation-15-16.txt**  
  - Remove special characters from `District` column using **regex**.  
  - Clean `Area` column (remove non-numeric characters).  

- **Tea-plantation-15-16.txt**  
  - Convert the **Sequence File** format (every 5th delimiter is replaced with a newline).  

- **Rubber-plantation-15-16.txt**  
  - Ensure correct data types are assigned.  

## 🔄 Data Transformation  
- Add **"Plantation Type"** column extracted from the filename.  
- Compute **"Productivity"** as:  
  ```
  Productivity = Production / Area
  ```
- Merge all datasets using **union()**.  

## 🔍 Analysis with PySpark  
- Data is ingested into **Spark DataFrames**.  
- Cleansing functions apply regex-based transformations.  
- **Spark SQL & Spark ML** are used to derive insights.  

## ✅ Evaluation Criteria  
✔ Data successfully ingested & converted to DataFrame.  
✔ Correct regex logic applied for cleaning.  
✔ Proper conversion of sequence files.  
✔ Transformation logic correctly implemented using **Spark SQL**.  
✔ Final results meet the case study’s objectives.  

## 📌 How to Run  
This code runs on **Microsoft Fabric Notebook**. Follow these steps:

1. Install dependencies:  
   ```python
   %pip install pyspark
   ```

2. Run the PySpark script in a Microsoft Fabric Notebook cell:  
   ```python
   from pyspark.sql import SparkSession

   spark = SparkSession.builder.appName("TN_Plantation_Analysis").getOrCreate()
   df = spark.read.csv("path/to/dataset.csv", header=True, inferSchema=True)
   df.show()
   ```  
   
## 📜 License  
This project is for educational purposes only.


