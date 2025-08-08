# Exploratory Data Analysis (EDA) — Hospitality Domain

This repository contains an end‑to‑end exploratory data analysis (EDA) of hotel bookings and operations data using Python (pandas). The goal is to clean, transform, and analyze booking and revenue data to generate actionable insights for the hospitality domain.

> Notebook: **`hotels_analysis.ipynb`**

## 🧱 Project Structure
```
.
├── hotels_analysis.ipynb        # Main analysis notebook
└── datasets/                    # Input CSVs (place here)
    ├── dim_date.csv
    ├── dim_hotels.csv
    ├── dim_rooms.csv
    ├── fact_bookings.csv
    ├── fact_aggregated_bookings.csv
    └── new_data_august.csv      # (optional / if available)
```
> The notebook can also read the CSVs from the project root (e.g., `dim_date.csv`) — but keeping all data under `datasets/` is recommended.

## 📦 Datasets
- **`dim_date.csv`** — Calendar/date dimension (daily grain; contains `date`, `mmm yy`, etc.).  
- **`dim_hotels.csv`** — Hotel attributes (static metadata).  
- **`dim_rooms.csv`** — Room attributes (capacity, type, etc.).  
- **`fact_bookings.csv`** — Booking‑level facts (check‑in/out, status, revenue).  
- **`fact_aggregated_bookings.csv`** — Pre‑aggregated KPIs by date/hotel/room (if provided).  
- **`new_data_august.csv`** — Additional monthly data (optional).

> Place these files in `datasets/` before running the notebook.

## 🔧 Environment & Setup
Use any recent Python 3.9+ environment.

```bash
# 1) Clone your repo
git clone https://github.com/Amgoth-Suresh/Exploratory-Data-Analysis-Using-Python-in-Hospitality-Domain.git
cd Exploratory-Data-Analysis-Using-Python-in-Hospitality-Domain

# 2) (Optional) Create and activate a virtual environment
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

# 3) Install dependencies
pip install -r requirements.txt

# 4) Launch Jupyter
jupyter notebook
# then open hotels_analysis.ipynb
```

### `requirements.txt`
This project currently uses **pandas** and **Jupyter** (the notebook relies primarily on pandas‑native APIs).
If you add plots later, install `matplotlib` or `seaborn` as needed.

```
pandas>=2.0
notebook
```

## 🗺️ Analysis Roadmap (Notebook Outline)
The notebook is organized into the following sections:

1. **Data Import and Exploration**  
   - Load CSVs (`pandas.read_csv`)  
   - Inspect shapes, dtypes, missingness, and basic descriptive stats

2. **Data Cleaning**  
   - Handle missing values / duplicates  
   - Type conversions (dates, numerics) and column standardization/renaming

3. **Data Transformation**  
   - Join fact tables with dimensions (date, hotel, rooms)  
   - Create analysis‑friendly columns (e.g., `mmm yy`, occupancy %, etc.)  
   - Aggregate to daily / monthly KPIs as needed

4. **Insights Generation**  
   - Booking trends by time period  
   - Occupancy and capacity utilization (`occ_pct`, `successful_bookings`, `capacity`)  
   - Revenue analysis (`revenue_realized`)  
   - Breakdown by hotel / room attributes / city

> Detected columns of interest in the notebook include: `date`, `check_in_date`, `mmm yy`, `successful_bookings`, `capacity`, `occ_pct`, `revenue_realized` (actual names may vary slightly).

## 📊 Key KPIs (typical for hospitality EDA)
- **Occupancy % (`occ_pct`)** = Rooms sold ÷ Rooms available  
- **Successful bookings** (after cancellations/no‑shows removed)  
- **Revenue realized** and revenue per period (daily/monthly)  
- **Capacity utilization** and seasonality by `mmm yy`  
- **City / hotel / room‑level comparisons**

> The current notebook focuses on EDA (no ML modeling). Add a modeling section later if you plan to forecast demand or cancellation risk.

## ▶️ How to Run
1. Ensure all listed CSVs exist in `datasets/` (or adjust file paths inside the notebook).  
2. Start Jupyter and open `hotels_analysis.ipynb`.  
3. Run all cells from top to bottom.  
4. Review outputs, tables, and derived KPIs. Export any final tables/plots if desired.

## 📝 Reproducibility
- Keep raw data read‑only and implement cleaning steps in code (already done in the notebook).  
- If you update data, re‑run the notebook end‑to‑end.  
- Pin a Python version and library versions (see `requirements.txt`).

## 📌 Next Improvements (nice to have)
- Add `matplotlib`/`seaborn` visualizations (time series, bar charts, heatmaps).  
- Publish a `Makefile` or simple script to run checks and regenerate outputs.  
- Add a `data_dictionary.md` describing all columns.  
- Provide sample outputs/figures in a `reports/` folder.

## 🤝 Contributing
Issues and pull requests are welcome. Please open an issue to discuss major changes first.

## 📄 License
Specify a license (e.g., MIT) or remove this section if private.

---

**Author:** Amgoth Suresh  
**Notebook:** `hotels_analysis.ipynb`
