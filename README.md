# 🚦 SDOT Collision Data Analysis

## 📄 Project Overview
This project analyzes the **Seattle Department of Transportation (SDOT) Collision Dataset** to identify patterns and risk factors that contribute to traffic collisions in Seattle.  
The focus is on understanding how **temporal trends**, **environmental conditions**, and **driver behaviors** (like speeding, inattention, and impairment) relate to collision types and severity.

---

## 🧹 Data Cleaning and Preparation
All preprocessing was performed in a separate notebook, **`scp-data-cleaning.ipynb`**, to ensure that all analyses use clean, reliable data.

### Steps Completed
- **Loaded raw SDOT dataset** (`SDOT_Collisions_All_Years_-681745443618578502.csv`)  
- **Initial checks:** inspected data types, missing values, and unique entries  
- **Removed irrelevant or redundant columns** (e.g., internal IDs, coordinates)  
- **Renamed columns** for clarity (`COLLISIONTYPE` → `collision_type`)  
- **Filled in missing values** for relevant columns where possible  
- **Removed null or invalid entries** from critical columns  
- **Replaced boolean indicators** (`True/False`, `0/1`) with readable values (`Yes/No`)  
- **Checked for and removed duplicate rows**  
- **Exported the cleaned dataset** as:
```

sdot_collision_comp.csv

```
### 🧾 Dataset Description

The cleaned dataset (`sdot_collision_comp.csv`) retains key descriptive and analytical fields from the SDOT collision data.  
It includes identification, context, and behavioral indicators for each reported collision.

#### Columns
| Column | Description |
|---------|-------------|
| `object_id` | Unique record identifier |
| `status` | Case status (e.g., Matched, Closed) |
| `address_type` | Type of address (Block, Intersection, etc.) |
| `location` | Collision location (text description) |
| `severity_code` | Numeric code representing collision severity |
| `severity_desc` | Severity description (e.g., Property Damage Only, Serious Injury, Fatal) |
| `collision_type` | Type of collision (e.g., Head-On, Rear-End, Sideswipe) |
| `person_ct` | Total number of people involved |
| `ped_ct` | Number of pedestrians involved |
| `ped_cycle_ct` | Number of bicyclists involved |
| `vehicle_ct` | Number of vehicles involved |
| `injury_ct` | Number of injuries reported |
| `serious_injury_ct` | Number of serious injuries |
| `fatal_ct` | Number of fatalities |
| `inc_date` | Date of the incident |
| `inc_datetime` | Full timestamp of the incident |
| `junction_type` | Type of road junction (e.g., Intersection, Mid-Block) |
| `sdot_col_code` | SDOT-specific collision code |
| `sdot_col_desc` | SDOT-specific collision description |
| `inattention_ind` | Indicates if inattention contributed to the collision (Y/N) |
| `und_infl_ind` | Indicates if the driver was under influence (Y/N) |
| `weather` | Weather condition at the time of collision |
| `road_cond` | Road surface condition |
| `light_cond` | Lighting condition (e.g., Daylight, Dark, Streetlights) |
| `speeding_ind` | Indicates if speeding was a contributing factor (Y/N) |
| `st_col_code` | State-level collision code |
| `st_col_desc` | State-level collision description |
| `seglane_key` | SDOT segment/lane key |
| `crosswalk_key` | SDOT crosswalk key |
| `hit_parked_car_ind` | Indicates if a parked vehicle was hit (Y/N) |
| `source_report_code` | Collision data source code |
| `source_desc` | Source description (e.g., Police Report) |

### Columns Used for Analysis
For the exploratory and statistical analysis in this project, a subset of these columns was used:
`year`, `month`, `hour`, `weather`, `road_cond`, `light_cond`, `collision_type`, `inattention_ind`, `und_infl_ind`, `speeding_ind`, `severity`
These fields were selected because they represent the most meaningful temporal, environmental, and behavioral factors associated with collision outcomes.

---

## 📂 Data Access
The original SDOT collision dataset is too large to include in this repository.  
To reproduce the results, download it directly from the official data portal:

🔗 **Official Dataset:**  
[SDOT Collisions All Years — Seattle Open Data Portal](https://catalog.data.gov/dataset/sdot-collisions-all-years-2a008)

### How to Set Up Your Data
1. Download the dataset as a CSV from the link above.  
2. Save it in the following folder structure:
```

SDOT_Collision_Analysis/
├── data/
│   └── SDOT_Collisions_All_Years_-681745443618578502.csv
├── code/
│   ├── scp-data-cleaning.ipynb
│   └── scp-trend-analysis.ipynb
└── README.md

```
3. Run the **data cleaning notebook** to generate:
```

sdot_collision_comp.csv

```
4. The **analysis notebook** uses `sdot_collision_comp.csv` for all visualizations and statistical analyses.

---

## 📊 Analysis Overview
All analysis is performed in **`scp-trend-analysis.ipynb`**, based on the cleaned dataset.

### Objectives
1. Explore **temporal patterns** (yearly, monthly, hourly trends).  
2. Examine **environmental conditions** (weather, road, and light conditions).  
3. Investigate **behavioral indicators** (`inattention_ind`, `speeding_ind`, `und_infl_ind`) and their relationship with collision type and severity.  
4. Apply **statistical tests** and **visualizations** to identify meaningful relationships.

### Example Analyses
- **Trend Analysis:** yearly/monthly/hourly changes in collisions.  
- **Environmental Factors:** collisions by weather, light, and road conditions.  
- **Behavioral Impact:** proportion of collisions involving speeding, inattention, or impairment.  
- **Statistical Testing:** Chi-square tests, correlation analysis, and ANOVA.

---

## 📈 Visualization Highlights
- **Countplots & Barplots** for collision counts by category  
- **Stacked Barplots** showing proportions by behavior  
- **Heatmaps** of collision types vs. risky behaviors  
- **Violin/Boxplots** for collision times vs. behaviors  
- **Risk Score Plots** combining multiple behaviors  

---

## 🧠 Tools & Libraries
| Category | Libraries Used |
|-----------|----------------|
| Data Processing | pandas, numpy |
| Visualization | matplotlib, seaborn |
| Statistics | scipy, statsmodels |
| Modeling | scikit-learn |
| Notebook Environment | Jupyter Notebook |

---

## 🪄 File Structure
```

📁 SDOT_Collision_Analysis
├── data/
│   ├── SDOT_Collisions_All_Years_-681745443618578502.csv           # (user-provided)
│   └── sdot_collision_comp.csv                                     # generated after cleaning  
├── notebooks/
│   ├── data_cleaning.ipynb
│   └── collision_analysis.ipynb
├── README.md
└── requirements.txt

````

---

## 📈 Future Work

* Incorporate **geospatial analysis** using latitude and longitude data
* Build an **interactive dashboard** using Plotly or Streamlit
* Develop a **predictive model** for collision severity

---

## 📚 References

* [Seattle Department of Transportation Open Data Portal](https://data.seattle.gov/)
* [SDOT Traffic Collisions Dataset](https://catalog.data.gov/dataset/sdot-collisions-all-years-2a008)
* Python libraries: pandas, numpy, seaborn, matplotlib, scipy, statsmodels, scikit-learn

---

💡 *This project aims to demonstrate a complete data workflow — from cleaning and preparation to exploratory analysis and visualization — on a real-world transportation safety dataset.*

```
