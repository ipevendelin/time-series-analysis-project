# Time-Series Analysis Report

## Project Overview
This document serves as the central reporting hub for the time-series analysis project. Analyses are added progressively as the project develops.

---

## 1. Time-Series Visualization and Exploratory Analysis (0.5p)

### Objective
Understand the basic characteristics of the time-series data through appropriate visualization and initial exploratory analysis.

### Key Components
- **Line plots**: Display temporal patterns and trends
- **Seasonal subseries plots**: Reveal repeating patterns across seasons/periods
- **ACF/PACF plots**: Identify potential autoregressive and moving average components
- **Descriptive statistics**: Mean, variance, min, max, quartiles

### Status
- [ ] Load and inspect dataset
- [ ] Create time-series line plot
- [ ] Generate seasonal subseries plots
- [ ] Calculate and display descriptive statistics
- [ ] Document initial observations

### Findings
#### Dataset: Bitcoin Historical Data (BTCUSD)
- **Time Period**: January 1, 2012 to November 6, 2025 (over 13 years)
- **Data Frequency**: 1-minute OHLCV (Open, High, Low, Close, Volume) candles
- **Total Records**: 7,283,197 observations
- **File Size**: ~382 MB

#### Closing Price Statistics
- **Mean Close**: $20,903.95
- **Median Close**: $7,213.85  
- **Min Close**: $3.80
- **Max Close**: $126,202.00
- **Std Dev**: $29,563.23

#### Daily Returns Analysis  
- **Mean Daily Return**: 0.2582%
- **Max Daily Gain**: 42.9224%
- **Max Daily Loss**: -48.0971%
- **Volatility (Std Dev)**: 3.4365%

#### Key Observations
1. Bitcoin has shown significant growth from $3.80 to $126,202 over the analysis period
2. High volatility with extreme moves reaching ±48% in daily changes
3. Positive average daily return indicates upward trend over the long term
4. Large gap between median and mean suggests right-skewed distribution with high-value outliers

---

## 2. Time-Series Decomposition Analysis (0.5p)

### Objective
Decompose the time-series into its constituent components: trend, seasonality, and residuals.

### Methodology
- **STL Decomposition** (Seasonal-Trend decomposition using LOESS)
- **Classical Decomposition** (additive or multiplicative)
- **Analysis of each component**

### Key Questions to Address
1. What is the underlying trend?
2. Is there a clear seasonal pattern? What is the periodicity?
3. Are there significant residuals?
4. Does the trend show structural breaks?

### Status
- [ ] Apply STL decomposition
- [ ] Apply classical decomposition (additive)
- [ ] Apply classical decomposition (multiplicative)
- [ ] Compare decomposition methods
- [ ] Analyze trend component
- [ ] Analyze seasonal component
- [ ] Analyze residual component

### Findings
#### Distribution Analysis: Daily Returns
- **Skewness**: -0.2889 (Negative skew indicates more extreme downward moves)
- **Kurtosis**: 21.5499 (High kurtosis indicates fat tails with extreme events)
- **Extreme Moves (>|5%|)**: 487 occurrences (9.63% of days)
  - Significant tail events in Bitcoin price movements
  - Non-normal distribution typical of crypto assets

#### Rolling Volatility Analysis (30-Day Window)
**Most Volatile Period**:
- Date: May 7, 2013
- Rolling Volatility: 18.0575%
- Event Context: Check Bitcoin market conditions around this date

**Least Volatile Period**:
- Date: June 4, 2012
- Rolling Volatility: 0.5404%
- Event Context: Stable market period (early Bitcoin era)

**Volatility Statistics**:
- Mean Rolling Volatility: 2.8437%
- Median Rolling Volatility: 2.4333%
- Max Rolling Volatility: 18.0575%
- Min Rolling Volatility: 0.5404%

#### Key Observations
1. High kurtosis (21.55) confirms fat tails in Bitcoin returns
2. Approximately 1 in 10 days experiences extreme >5% moves
3. Volatility has varied dramatically from 0.54% to 18.06% over time
4. More recent periods show elevated but stabilizing volatility compared to 2013 peaks

---

## 3. Autocorrelation Analysis (0.5p)

### Objective
Analyze the autocorrelation structure to understand temporal dependencies in the data.

### Methodology
- **Autocorrelation Function (ACF)**: Measures correlation between observations at different lags
- **Partial Autocorrelation Function (PACF)**: Removes intermediate effects to show direct correlations
- **Ljung-Box test**: Tests for overall significance of autocorrelation

### Expected Outcomes
- ACF plot showing significant lags
- PACF plot showing direct correlations
- Identification of AR and MA orders
- Assessment of stationarity needs

### Status
- [ ] Calculate ACF
- [ ] Calculate PACF
- [ ] Plot ACF and PACF
- [ ] Perform Ljung-Box test
- [ ] Identify significant lags
- [ ] Assess stationarity requirements

### Findings
#### Autocorrelation Analysis Status

**Analysis Planned**: This section will include:
- ACF and PACF plots identifying significant lags
- Ljung-Box test results for overall autocorrelation significance
- Assessment of stationarity requirements
- Identification of potential AR and MA orders
- Discussion of memory in Bitcoin price movements

**Data Ready**: Daily returns series prepared and cleaned
- Ready for ACF/PACF calculation
- Data span: 4,746 trading days
- No missing values in returns series

**Expected Insights**:
- Determine if Bitcoin returns follow random walk
- Assess how many previous days affect future returns
- Evaluate suitability for ARIMA-type models

---

## 4. Data Partitioning Plan for Model Formation (0.5p)

### Objective
Develop a strategy for partitioning the time-series data into training, validation, and test sets, considering the temporal nature of the data.

### Partitioning Strategy

#### Standard Approach (If data size permits)
- **Training Set**: 60-70% of historical data
- **Validation Set**: 10-15% of data (middle period)
- **Test Set**: 15-20% of most recent data

#### Time-Series Cross-Validation
- **Forward-chaining method**: Use growing training windows
- **Initial training period**: First 60% of data
- **Validation window**: Fixed size (e.g., 10% of data)
- **Slide forward**: Move validation window forward one period at a time

### Justification
1. **Temporal order preservation**: Maintains natural time sequence
2. **Realistic evaluation**: Test set uses only future data (no look-ahead bias)
3. **Multiple validation scenarios**: Forward-chaining tests robustness
4. **Seasonal coverage**: Sufficient data to capture seasonal patterns

### Proposed Partition

#### Bitcoin Historical Data: Daily Returns Series

**Total observations**: 4,746 trading days (January 1, 2012 to November 6, 2025)
**Training set size**: 2,848 days (60%)
**Validation set size**: 713 days (15%)
**Test set size**: 1,185 days (25%)

**Date Ranges**:
- Training: 2012-01-01 to 2019-07-13
- Validation: 2019-07-14 to 2021-09-25
- Test: 2021-09-26 to 2025-11-06

```
Total observations: [TO BE FILLED]
Training set size: [TO BE FILLED] (60-70%)
Validation set size: [TO BE FILLED] (10-15%)
Test set size: [TO BE FILLED] (15-20%)
```

### Cross-Validation Plan

```
Window 1: Train on obs 1-50%, validate on obs 50-60%
Window 2: Train on obs 1-60%, validate on obs 60-70%
Window 3: Train on obs 1-70%, validate on obs 70-80%
Window 4: Train on obs 1-80%, validate on obs 80-90%
Final: Train on obs 1-90%, test on obs 90-100%
```

### Status
- [ ] Determine data size and frequency
- [ ] Define partition percentages
- [ ] Specify date ranges for each partition
- [ ] Plan cross-validation windows
- [ ] Document rationale

### Findings
*To be added after analysis*

---

## Summary

### Completed Analyses
*Updates as analyses are completed*

### Next Steps
1. Complete exploratory analysis
2. Perform decomposition
3. Conduct autocorrelation analysis
4. Finalize data partitioning
5. Develop forecasting models

### Key Learnings
*To be documented*

---

## References

- [Time-Series Decomposition (Python)](https://www.statsmodels.org/dev/examples/notebooks/generated/stl_decomposition.html)
- [Time-Series Decomposition (MATLAB)](https://se.mathworks.com/help/matlab/ref/double.trenddecomp.html)
- [Partition of Time-Series Data (MATLAB)](https://se.mathworks.com/help/stats/tspartition.html)
- [Cross-Validation in Time-Series](https://medium.com/@soumyachess1496/cross-validation-in-time-series-566ae4981ce4)
- [Autocorrelation Analysis (MATLAB)](https://se.mathworks.com/help/econ/autocorr.html)
- [Autocorrelation Analysis (Python)](https://www.geeksforgeeks.org/how-to-calculate-autocorrelation-in-python/)
