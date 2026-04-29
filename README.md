# Metro_analysis
# Delhi Metro Dataset — Exploratory Data Analysis

A comprehensive dataset and analysis of the Delhi Metro Rail Network, covering **285 stations** across **13 lines** with geospatial, temporal, and infrastructure attributes.

---

## Dataset

**File:** `Delhi_metro.csv`  
**Rows:** 285 stations  
**Columns:** 8

| Column | Description |
|---|---|
| `ID (Station ID)` | Unique station identifier |
| `Station Names` | Name of the station |
| `Dist. From First Station(km)` | Distance in km from the first station on that line |
| `Metro Line` | Metro line the station belongs to |
| `Opened(Year)` | Date the station was inaugurated |
| `Layout` | Infrastructure type — `Elevated`, `Underground`, or `At-Grade` |
| `Latitude` | Geographic latitude |
| `Longitude` | Geographic longitude |

---

##  Key Facts

| Metric | Value |
|---|---|
| Total stations | 285 |
| Total metro lines | 13 |
| Network span (longest line) | 52.7 km (Blue line) |
| First station opened | 2002 |
| Latest expansion | 2019 |
| Station closest to city centre | Rajiv Chowk (0.21 km) |

---

## Analysis Covered

### Network Overview
- Total length (km) covered by each metro line
- Stations per line and cumulative growth over time
- Year-by-year expansion of the network

### Performance Metrics
- Stations per km and average interstation distance per line
- Longest and shortest average gaps between stations
- Farthest station from the first station on each line

### Spatial Analysis
- Geographic distribution of stations across Delhi
- Regional coverage — North, South, East, West, Central
- Identification of underserved areas (gaps > 2 km)
- Station closest to Connaught Place (city centre)

### Infrastructure Analysis
- Infrastructure type (Elevated / Underground / At-Grade) by line and year
- Trend of underground construction over the decades

---

## Requirements
```
Pandas
Numpy
Seaborn
matplotlib
folium
```
## How to Run

**1. Clone the repository**
```bash
git clone https://github.com/your-username/delhi-metro-analysis.git
cd delhi-metro-analysis
```

**2. Create a virtual environment (recommended)**
```bash
# Mac/Linux
python -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
venv\Scripts\activate
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Make sure the dataset is in the project root**
```
delhi-metro-analysis/
│
├── Delhi_metro.csv        ← dataset
├── requirements.txt       ← dependencies
├── README.md              ← documentation
└── analysis.py            ← your analysis scripts
```

**5. Run the analysis**
```bash
python analysis.py

---

## Quick Start

```python
import pandas as pd

df = pd.read_csv('Delhi_metro.csv')
df['Year'] = pd.to_datetime(df['Opened(Year)'], dayfirst=True).dt.year

# Total length per line
print(df.groupby('Metro Line')['Dist. From First Station(km)'].max().sort_values(ascending=False))

# Stations opened per year
print(df.groupby('Year').size())
```

---


## Metro Lines

| Line | Stations | Length (km) | Dominant Infrastructure |
|---|---|---|---|
| Blue line | 49 | 52.7 | Elevated |
| Pink line | 38 | 52.6 | Mixed |
| Yellow line | 37 | 45.7 | Mixed |
| Violet line | 34 | 43.5 | Mixed |
| Magenta line | 25 | 33.1 | Underground |
| Red line | 29 | 32.7 | Elevated |
| Aqua line | 21 | 27.1 | Elevated |
| Green line | 21 | 24.8 | Elevated |
| Orange line | 6 | 20.8 | Underground |
| Rapid Metro | 11 | 10.0 | Elevated |
| Blue line branch | 8 | 8.1 | Elevated |
| Gray line | 3 | 3.9 | Mixed |
| Green line branch | 3 | 2.1 | Elevated |

---

## Key Insights

- **Blue line** is the longest and most station-dense line at 52.7 km with 49 stations
- **Orange line** (Airport Express) has the largest average gap between stations (4.16 km) by design
- **Rajiv Chowk** is the closest station to Delhi's city centre and the main interchange hub
- **2010 and 2018** were the biggest expansion years — 54 and 64 stations added respectively
- **North Delhi** is significantly underserved compared to South and Central Delhi
- Underground construction peaked in **2018**, reflecting expansion into dense urban corridors

---
