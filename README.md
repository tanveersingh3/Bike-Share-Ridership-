# Cyclistic Bike-Share: Rider Behavior Analysis

A case-study style analysis of Cyclistic's bike-share trip data, aimed at understanding how **annual members** and **casual riders** use the service differently — and turning that into marketing recommendations for converting casual riders into members.

## Business Task

Annual members are more profitable than casual riders for Cyclistic. The goal of this analysis is to identify behavioral differences between the two rider types and design a marketing strategy that converts casual riders into annual members.

## Interactive Dashboard

View the full Tableau dashboard live here: **[Cyclistic Dashboard on Tableau Public](https://public.tableau.com/views/Cyclistic_17759838837060/Dashboard1?:language=en-US&publish=yes)**

## Repo Contents

| File | Description |
|---|---|
| `cyclistic_cleaning.ipynb` | Jupyter notebook covering data collection, cleaning, and exploratory analysis |
| `cyclistic-bike-share-rider-behavior-analysis.pptx` | Final stakeholder-facing presentation summarizing insights and recommendations |

> The Tableau workbook (`.twbx`) is hosted on Tableau Public (linked above) rather than in this repo, since the packaged file exceeds GitHub's file size limit.

## Data & Cleaning

The raw data consists of 12 months of Cyclistic trip data (`data1.csv`–`data12.csv`), combined into a single dataset indexed by `ride_id`. Cleaning steps included:

- Concatenating all 12 monthly files into one dataframe
- Converting `started_at` / `ended_at` to proper datetime types
- Dropping rows with missing end-location coordinates (~0.1% of data)
- Deriving `ride_duration` (and `ride_minutes`) from start/end timestamps
- Removing rides with negative or zero duration, and outlier rides over 24 hours (likely docking errors or lost/stolen bikes)
- Engineering features for analysis: `day_of_week`, `month`, `hour`, and `time_of_day` (Morning / Afternoon / Evening / Night)

The cleaned dataset was exported to `full_data.csv`, along with normalized breakdowns by month, weekday, and time of day for use in Tableau.

## Key Findings

- **Members drive volume, casuals drive duration.** Members take more rides overall, but casual riders' individual trips are longer — casuals average ~19.9 minutes per ride vs. ~12.2 minutes for members (about 62% longer).
- **Bike preference differs by usage pattern.** Electric bikes account for more total rides, but the longest rides — especially among casual riders — happen on classic bikes.
- **Weekends shift the balance.** Ride counts between members and casuals become nearly equal on weekends, with casuals taking noticeably longer trips — consistent with leisure use rather than commuting.
- **Casual ridership is highly seasonal.** Activity for both groups peaks in summer (June–August), but casuals show a much sharper rise and fall — and a far steeper drop-off (~12x) heading into winter compared to members (~4x).
- **Time-of-day usage differs by rider type.** Members ride fairly consistently throughout the day (commute + leisure), while casual riders skew heavily toward afternoon rides.

Full observations and interpretations are documented in the notebook and presentation.

## Recommendations

1. **Targeted seasonal and location-based marketing** — Run campaigns at high-traffic weekend/summer locations (parks, tourist spots, lakefronts), framing membership as a way to save money on the riding casuals are already doing.
2. **Time-targeted digital advertising** — Since casual riders are most active in the afternoon, push social/app ads and limited-time membership offers during peak casual riding hours.
3. **Cost comparison marketing** — Show casual riders how their per-ride spending compares to the cost of an annual membership, using ride duration/frequency data to make the case directly.

## Tools Used

- **Python (pandas)** — data cleaning, feature engineering, and exploratory analysis
- **Tableau** — visualization and dashboarding
- **PowerPoint** — final stakeholder presentation

## How to Reproduce

1. Place the 12 monthly `dataN.csv` trip data files in the same directory as the notebook
2. Run `cyclistic_cleaning.ipynb` top to bottom to produce `full_data.csv` and the normalized summary CSVs
3. Explore the dashboards on [Tableau Public](https://public.tableau.com/views/Cyclistic_17759838837060/Dashboard1?:language=en-US&publish=yes), or load the exported CSVs into Tableau Desktop to rebuild them
