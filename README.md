# Gold Macro

Macro stress indicators and commodity–gold relationships using
World Bank Pink Sheet data.

## Methods
- Macro Stress Indicator (MSI)
- Regime-based returns (high vs low stress)
- Correlation & rolling correlation analysis

## Data
World Bank CMO Historical Monthly Data

# Gold Macro

A macroeconomic analysis project exploring the relationship between **gold** and **global macro stress**, using **World Bank Pink Sheet (CMO) monthly commodity data**.

The project constructs a **Macro Stress Indicator (MSI)** from key commodities (energy, metals, agriculture) and studies how gold behaves across different macro stress regimes.

---

## Motivation

Gold is often viewed as:
- a **safe-haven asset**
- an **inflation hedge**
- a **macro risk diversifier**

However, its behavior depends heavily on the **macro environment**.  
This project asks:

- Can we quantify macroeconomic stress using commodity markets?
- How does gold behave during **high-stress vs low-stress** regimes?
- Is gold’s return profile meaningfully different when macro stress is elevated?

---

## Data

**Source**
- World Bank – *Commodity Markets Outlook (CMO) Historical Monthly Data*
- Also known as the **Pink Sheet**

**Coverage**
- Monthly frequency
- 1960 → 2025
- 70+ global commodity price series

**Key categories**
- Energy (crude oil, natural gas, coal)
- Industrial metals
- Precious metals (gold, silver, platinum)
- Agricultural commodities (grains, food staples)

> Raw data files are intentionally excluded from version control.

---

## Project Structure

gold_macro/
│
├── notebooks/
│ └── 01_explore.ipynb # Exploratory analysis, MSI construction, plots
│
├── src/
│ ├── load_prices.py # Data loading & cleaning utilities
│ ├── features.py # Feature engineering helpers
│ └── rolling.py # Rolling statistics & correlations
│
├── .gitignore
├── README.md



---

## Methodology

### 1. Data Cleaning & Alignment
- Parse multi-row headers from the Pink Sheet
- Convert dates to month-end timestamps
- Coerce numeric columns and align time series
- Handle missing data conservatively

---

### 2. Macro Stress Indicator (MSI)

The **MSI** is constructed as follows:

1. Select a basket of macro-sensitive commodities:
   - Energy (oil benchmarks)
   - Industrial metals
   - Agricultural staples

2. Compute **monthly returns** for each series

3. Standardize returns (z-scores)

4. Aggregate across commodities:
   - Equal-weighted average of standardized returns

The resulting MSI captures **systemic commodity price stress** rather than idiosyncratic moves.

**Interpretation**
- MSI > 0 → Above-average macro stress
- MSI < 0 → Below-average macro stress

---

### 3. Regime-Based Analysis

Macro regimes are defined using MSI quantiles:

- **High-stress regime**: MSI > 75th percentile
- **Low-stress regime**: MSI < 25th percentile

Gold returns are then compared across regimes.

---

### 4. Correlation Analysis

Multiple approaches are used:
- Static correlations
- Rolling correlations
- Regime-conditional correlations

This avoids relying on a single summary statistic.

---

## Key Findings

- Gold exhibits **stronger average returns during high macro stress regimes**
- The relationship is **state-dependent**, not constant through time
- Commodity-driven macro stress provides a useful lens for understanding gold behavior
- Rolling correlations highlight regime shifts rather than stable long-run relationships

*(Exact numerical results depend on sample period and commodity basket.)*

---

## Visualizations

The project includes:
- Time series plots of MSI
- Gold price and return plots
- Rolling correlation charts
- Regime comparison plots (high vs low stress)

All visualizations are generated in the analysis notebook.

---

## Tools & Libraries

- Python 3.11
- pandas
- numpy
- matplotlib
- statsmodels

---

## Extensions & Future Work

Potential extensions:
- Add inflation and interest rate data
- Compare gold vs silver during stress
- Build a real-time MSI update pipeline
- Test MSI as a predictor for other asset classes
- Apply PCA or factor models to commodity stress



