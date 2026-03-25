# Metro-Ridership-Analysis

An end-to-end data analysis project on **Bengaluru's Namma Metro** ridership patterns, covering data collection, preprocessing, exploratory analysis in Python, and interactive dashboarding in Power BI.

---

## Project Overview

This project analyzes daily ridership data for Namma Metro (Bengaluru Metro Rail Corporation) from **October 2024 to March 2025**. It explores how different ticket types, days of the week, and significant events (holidays, concerts, public events) influence passenger volumes across the network.

---

## Files

| File | Description |
|------|-------------|
| `NammaMetro_Ridership_Dataset.csv` | Raw daily ridership data (131 records, Oct 2024 – Mar 2025) |
| `NammaMetro_Ridership_Processed.csv` | Cleaned and feature-engineered dataset used for analysis and Power BI |
| `bangalore_metro_stations.csv` | Complete station list across all metro lines with interchange flags |
| `metro_stations.py` | Python dictionary mapping all metro lines to their stations and interchange points |
| `significant_dates.csv` | Calendar of notable events (holidays, concerts, sporting events) mapped to dates |
| `Metro.ipynb` | Main analysis notebook — EDA, preprocessing, and visualizations |
| `py_to_csv.ipynb` | Utility notebook to export `metro_stations.py` data to CSV |

---

## Dataset

### Raw Ridership (`NammaMetro_Ridership_Dataset.csv`)
131 daily records with the following ticket-type breakdowns:

- **Smart Cards** — Stored Value Card, 1-Day Pass, 3-Day Pass, 5-Day Pass
- **Tokens** — Single-journey paper tokens
- **NCMC** — National Common Mobility Card
- **QR Codes** — NammaMetro app, WhatsApp, Paytm
- **Group Tickets**

### Processed Dataset (`NammaMetro_Ridership_Processed.csv`)
Engineered features added during preprocessing:

- `Day of Week` — Monday through Sunday
- `Traffic Band` — Weekday / Weekend Lite (Fri/Sat) / Weekend (Sun)
- `Smart Cards` — Combined smart card total
- `NCMC` — NCMC total
- `Commute` — Smart Cards + NCMC (regular commuter proxy)
- `Tokens` — Token total
- `QR` — Total QR ridership
- `Group Ticket` — Group ticket count
- `Casual` — Tokens + QR + Group Tickets (casual/tourist rider proxy)
- `Total` — Overall daily ridership

### Metro Network (`metro_stations.py` / `bangalore_metro_stations.csv`)
Full station data across **7 lines**:

| Line | Status | Stations |
|------|--------|----------|
| Purple Line | Operational | 37 stations (Challaghatta ↔ Whitefield) |
| Green Line | Operational | 32 stations (Silk Institute ↔ Madavara) |
| Blue Line | Planned (TBC) | 30 stations (KIAL ↔ Central Silk Board) |
| Yellow Line | Planned (TBC) | 16 stations (RV Road ↔ Bommasandra) |
| Pink Line | Planned (TBC) | 18 stations (Kalena Agrahara ↔ Nagawara) |
| Orange Line | Planned (TBC) | 22 stations (JP Nagar ↔ Kempapura) |
| Grey Line | Planned (TBC) | 9 stations (Hosahalli ↔ Kadabagere) |

**15 interchange stations** are identified where lines intersect (e.g., Majestic, MG Road, Krishnarajapura).

---

## Analysis (`Metro.ipynb`)

### Data Cleaning
- Removed duplicate records, keeping the latest entry per date
- Parsed and standardized date formats
- Cast numeric columns to nullable `Int64`

### Feature Engineering
- Derived `Day of Week` and `Traffic Band` from record dates
- Aggregated ticket types into `Commute`, `Casual`, and `Total` ridership buckets

### Exploratory Analysis
- Descriptive statistics across all ticket categories
- Daily ridership trends over the 5-month window
- Weekday vs. weekend ridership patterns
- Impact of significant events on ridership spikes/dips
- Ticket type share analysis (Smart Card vs. Token vs. QR)
- NCMC adoption trend over time

---

## Significant Events Tracked

The `significant_dates.csv` file maps events to dates for anomaly context:

- **Holidays**: Diwali, Christmas, New Year's, Republic Day, Holi, Ugadi, Eid, etc.
- **Local Events**: Rajyotsava Day, Makara Sankranti, Kannada Rajyothsava
- **Special Events**: Ed Sheeran Concert (Feb 8–9), Aero India 2025 (Feb 10–14), Ranji Trophy, Champions Trophy Final
- **Operational Changes**: Fare Hike (Feb 9, 2025)

---

## Power BI Dashboard

An interactive Power BI report was built on top of `NammaMetro_Ridership_Processed.csv` and `significant_dates.csv`, featuring:

- Daily ridership trend line with event annotations
- Ticket type breakdown (donut/bar charts)
- Weekday vs. weekend comparison
- Traffic band distribution
- NCMC growth over time
- Ridership impact analysis around significant dates

---

## Tech Stack

- **Python** — pandas, numpy, matplotlib, seaborn
- **Jupyter Notebooks** — EDA and preprocessing
- **Power BI** — Interactive dashboarding
- **Data Source** — Namma Metro (BMRCL) public ridership reports

---

## Key Insights

- Weekday ridership consistently outperforms weekends, averaging ~860K vs ~630K trips
- Smart Cards dominate (~48% share), followed by Tokens (~27%) and QR (~23%)
- NCMC adoption grew steadily from ~7K/day in Oct 2024 to ~22K/day by Mar 2025
- Events like Aero India and Republic Day caused notable ridership shifts
- The Feb 2025 fare hike had a measurable short-term impact on token and QR usage
- New Year's Eve (Dec 31) saw a significant token spike due to extended service hours
