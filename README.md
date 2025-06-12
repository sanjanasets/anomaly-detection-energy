# Unsupervised Anomaly Detection in Household Energy Usage

## Project Overview

This project explores **unsupervised anomaly detection** using machine learning to analyze household energy usage patterns. The goal was to build a model that can learn what “normal” multivariate energy behavior looks like — and then flag timestamps when energy usage becomes abnormal.

The analysis uses the **UCI Individual Household Electric Power Consumption** dataset, focusing on detecting unusual activity across key energy metrics like global active power, voltage, and sub-metered appliance usage.

---

## Project Goal

> **Can I build a model that learns what ‘normal’ energy behavior looks like across multiple features — and then flags timestamps when things behave strangely?**

This is especially valuable in real-world scenarios like energy monitoring, equipment fault detection, and smart home automation — where anomalies may reflect outages, unusual consumption habits, or malfunctioning appliances.

---

## Tools & Technologies

- **Python** (v3.12)
- **Pandas** for data manipulation
- **Matplotlib / Seaborn** for visualization
- **scikit-learn** for modeling (`IsolationForest`, `StandardScaler`)
- **Statsmodels** (optional) for time series decomposition

---

## Dataset

- **Source**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption)
- **Timeframe**: December 2006 – November 2010
- **Granularity**: Minute-level data (resampled to hourly for this project)
- **Features used**:
  - `Global_active_power`
  - `Voltage`
  - `Global_reactive_power`
  - `Sub_metering_1`, `Sub_metering_2`, `Sub_metering_3`

---

## Exploratory Analysis Highlights

- The data shows strong daily and seasonal usage patterns.
- `Global_active_power` is **right-skewed**, with most usage under 1kW.
- Voltage fluctuates between 230V–250V with some low dips.
- Correlation analysis revealed:
  - Strong link between `Global_active_power` and `Sub_metering_3`
  - Inverse relationship between `Voltage` and current-based features

---

## Modeling Approach

- **Model**: `IsolationForest` (unsupervised outlier detection)
- **Contamination**: 1% (assumes ~1% of data are anomalies)
- **Input**: Scaled multivariate data
- **Output**: Binary anomaly flag (`is_anomaly`) and anomaly scores

### Results

Anomalies detected included:
- High-usage spikes (e.g., multiple appliances)
- Unusual low-usage periods (e.g., suspected outages or absences)
- Voltage dips potentially indicating grid or appliance issues

---

## Visual Insights

Plots were created to overlay anomalies on:
- **Global Active Power**
- **Voltage**

These clearly illustrated when and how the model identified outliers, providing strong visual validation.

---

## Conclusion

The project demonstrates the value of using **unsupervised machine learning** to surface meaningful anomalies in household energy data. Even without labeled anomaly data, the model effectively identified deviations from normal behavior across time.

---

## Future Work

- Explore **Autoencoder-based anomaly detection**
- Add **real-time detection capability**
- Build a **Streamlit dashboard** for interactive anomaly exploration
- Extend analysis to other sensors (e.g., temperature, occupancy)

---

## Author

**Sanjana Settipalli**   

