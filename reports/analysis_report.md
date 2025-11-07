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
*To be added after analysis*

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
*To be added after analysis*

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
*To be added after analysis*

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

*To be specified after data analysis:*

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
