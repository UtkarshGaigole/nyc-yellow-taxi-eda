# NYC Yellow Taxi EDA – 2023

## 📌 Objective
This project performs **Exploratory Data Analysis (EDA)** on New York City Yellow Taxi ride data for the year 2023.  
The goal is to demonstrate why EDA is a crucial step in the **data science** and **machine learning** workflow, uncover patterns and trends, and generate actionable insights for taxi operations.

---

## 📂 Project Structure

```
├── notebooks/
│   ├── 01_data_sampling.ipynb         # Data loading and sampling
│   ├── 02_data_cleaning.ipynb         # Data preprocessing and cleaning
│   └── 03_exploratory_analysis.ipynb  # EDA, visualizations, and insights
├── NYC_Yellow_Taxi_Executive_Summary.pdf  # Executive summary of analysis
└── README.md                          # Project description and usage
```

> **Note:** The dataset is **too large** to be stored in this repository.  
You can download it directly from the [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) website if you wish to replicate the analysis.

---

## 📊 Dataset Description

The **Yellow Taxi Trip Records** dataset contains information on pick-up and drop-off dates/times, locations, trip distances, fares, rate types, payment types, and passenger counts.

- **Source:** [NYC Taxi & Limousine Commission Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)  
- **Data Format:** Parquet (`.parquet`)  
- **Time Range:** January 2023 – December 2023  
- **Data Fields:** See [Data Dictionary](https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf)  

Key columns include:
- `tpep_pickup_datetime`, `tpep_dropoff_datetime`
- `passenger_count`, `trip_distance`
- `PULocationID`, `DOLocationID`
- `fare_amount`, `tip_amount`, `total_amount`
- `payment_type`, `RatecodeID`
- `airport_fee`, `congestion_surcharge`, `MTA_tax`, `extra`

---

## 🛠️ Methodology

### **1. Data Sampling**
- Loaded monthly Parquet files for 2023  
- Applied **hourly stratified sampling (5%)** to create a representative dataset  
- Combined sampled data into a single DataFrame  

### **2. Data Cleaning**
- Fixed inconsistent columns (e.g., `airport_fee` merge)  
- Removed negative and unrealistic values  
- Imputed missing values:
  - **Passenger count:** random weighted sampling from observed distribution  
  - **RatecodeID & congestion_surcharge:** filled with median values  
- Removed outliers in trip distance, fare amount, and tip amount  

### **3. Exploratory Data Analysis**
- Time-based demand analysis (hourly, daily, monthly)  
- Revenue trends & seasonal patterns  
- Fare vs. distance and fare vs. duration relationships  
- Payment type distribution  
- Geospatial analysis with NYC taxi zones shapefile  
- Passenger count patterns across time and zones  
- Surcharge frequency and impact  

---

## 📈 Key Insights

- **Peak Demand Hours:** 5 PM – 7 PM on weekdays, steady leisure demand on weekends  
- **Busiest Zones:** Midtown Manhattan, JFK Airport, LaGuardia Airport  
- **Revenue Trends:** Q2 and Q4 have highest revenues; higher fares in afternoon/evening  
- **Fare Structure:** Strong correlation between distance and fare; short trips have higher cost per mile  
- **Payment Methods:** Majority via credit card (>90%)  
- **Tipping Behavior:** Evening trips see higher tip percentages  

---

## 📦 Requirements

Create a `requirements.txt` file with:

```
pandas
numpy
matplotlib
seaborn
geopandas
shapely
pyarrow
```

---

## ▶️ How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/nyc-yellow-taxi-eda.git
   cd nyc-yellow-taxi-eda
   ```

2. **Download the Dataset**  
   Retrieve `.parquet` files for each month of 2023 from the  
   [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) website  
   and place them in a `dataset/` folder in the repository root.

3. **Open Notebooks**
   - Run in **Jupyter Notebook** or **Google Colab**  
   - Follow in order:
     - `01_data_sampling.ipynb`
     - `02_data_cleaning.ipynb`
     - `03_exploratory_analysis.ipynb`

---

## 📜 License
This project is for educational and analytical purposes.  
Dataset is provided by NYC TLC under their [Terms of Use](https://www.nyc.gov/assets/tlc/downloads/pdf/trip_record_user_guide.pdf).

---

## 🙌 Acknowledgements
- [NYC Taxi & Limousine Commission](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) for providing the dataset  
- Python libraries: **pandas, numpy, matplotlib, seaborn, geopandas**
