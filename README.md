# Delhi Air Quality Index (AQI) Analysis

ShadowFox Data Science Internship — **Intermediate Task 1**

## Overview
Analysis of hourly Delhi air-pollution data (1–24 Jan 2023, 561 records, 8 pollutants) to identify the key pollutants, how air quality varies over time, and what the pollutant relationships suggest about sources. The AQI is computed with the official **CPCB (India) method**.

## Research questions
1. **Key pollutants** – which pollutants drive the AQI and how far do they exceed NAAQS / WHO limits?
2. **Temporal variation** – how does air quality vary across the day and the month?
3. **Source signatures** – what do pollutant correlations and weekday/weekend differences suggest?

## Headline results
- Every hour was *Very Poor* (24.9%) or *Severe* (75.1%); **PM2.5 was the dominant pollutant in 100% of hours**.
- Mean PM2.5 ≈ 358 µg/m³ — about 6× the NAAQS 24-h limit and 24× the WHO guideline; all 22 complete days exceeded the NAAQS for PM2.5 and PM10.
- PM2.5 is ~85% of PM10 and tracks CO (ρ = 0.89) and NO₂ (ρ = 0.67) → combustion-related sources.
- Strong daily cycle: lowest ≈ 13:00 IST (≈194 µg/m³), highest ≈ 22:00 IST (≈540 µg/m³) (Kruskal-Wallis p < 10⁻¹⁴).
- Weekdays were more polluted than weekends (PM2.5 394 vs 261 µg/m³) — suggestive only (16 vs 6 days).

## Limitations
The file covers one winter month at one unnamed location with no weather data, so **seasonal variation and geographical factors could not be tested**. Timestamps appear to be UTC and were converted to IST (inferred from the ozone peak). The AQI is capped at 500, which flattens the worst hours. See the notebook (Section 11).

## Repository contents
| File | Description |
|---|---|
| `Delhi_AQI_Analysis.ipynb` | Full analysis notebook (code, outputs, interpretation) |
| `delhiaqi.csv` | Input dataset |
| `delhi_aqi_hourly_with_cpcb_aqi.csv` | Hourly data with computed AQI, dominant pollutant, category |
| `figures/` | Saved charts used in the notebook |

## How to run
```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter notebook Delhi_AQI_Analysis.ipynb   # run all cells; keep delhiaqi.csv in the same folder
```
