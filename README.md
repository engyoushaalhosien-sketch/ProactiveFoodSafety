# ProactiveFoodSafety
Specializing in food safety, aim to shift from traditional reactive methods to a proactive approach that leverages intelligent data analysis and ML to predict risks. I support organizations in developing their systems, proactively detecting deviations, reducing reliance on manual inspections, towards sustainable and responsive food safety.
# Milk Pasteurization Monitoring (HACCP) 🥛🔥

Analyzing and monitoring the **milk pasteurization** process using Python and Jupyter Notebook (Google Colab).

The project focuses on:

1) **Data Exploration** and plotting time series data for process variables.

2) **Verifying HACCP Control Limits/Critical Limits** (e.g., pasteurization time ≥ 15 seconds and temperature not below a specified limit).

3) **Anomaly Detection** using the `IsolationForest` model to identify operational deviations.

4) **Incident Interpretation** by ranking variables according to their relative contribution to each anomaly and generating a CSV report for operational use.

> Suitable for quality, food safety, and dairy processing teams.

---

## 📁 Data

- **Input File Format**: CSV

- **Expected Columns (Typical)**:

- `Timestamp` (Date/Time)

- `Inlet_Temp` — Inlet Temperature (°C)

- `Heating_Section_Temp` — Heating Section Temperature (°C)

- `Holding_Tube_Temp` — Holding Tube Temperature (°C)

- `Outlet_Temp` — Outlet Temperature (°C)

- `Flow_Rate_LPH` — Flow Rate (L/h)

- `Differential_Pressure` — Differential Pressure

- `Milk_Conductivity` — Milk Conductivity

- `pH_Level` — pH

- `Pump_Speed_RPM` — Pump Speed ​​(RPM)

- `Valve_Position_Pct` — Valve Position (%)

- `Pasteurization_Time_Sec` — **Pasteurization Time in Seconds** (Basic Variable)

> You can modify the column names in the first cell of the workbook to match your file.

---

## 🧭 Methodology

1. **Scaling and Calibration**

- Convert the `Timestamp` to a date format.

- Use `StandardScaler` to standardize the scales before modeling.

2. **Evidence-based Exploration (EDA)**

- Linear plots of the time series (Temperatures, Flow, Valve, etc.).

- A distribution plot of the pasteurization time with a **critical boundary line** (e.g., 15 seconds).

- A **Heatmap** of the variables; often, a **strong negative** correlation is shown between `Flow_Rate_LPH` and `Pasteurization_Time_Sec` (i.e., the higher the flow rate, the shorter the dwell time).

3. **HACCP Limits**

- Verify the **minimum pasteurization time** (typically 15 seconds).

- Verify the **minimum temperature** (e.g., ~71.8°C – adjustable according to facility specifications).

4. **Anomaly Detection**

- Use `IsolationForest` (configurable parameters: `n_estimators`, `contamination`, …).

- Calculate the anomaly score and assign a `-1` label to anomalies.

- **Incident Interpretation**: Rank the variables that contributed to the anomaly (a simplified approach based on post-standardization metrics and/or their divergence from “normal” behavior) to produce the following fields:

- `Primary_Cause`, `Secondary_Cause`, `Tertiary_Cause` with an estimated contribution percentage (%).

5. **Output**

- A CSV file named `HACCP_Pasteurization_Analysis.csv` containing:

`Timestamp`, `Primary_Cause(%)`, `Secondary_Cause(%)`, `Tertiary_Cause(%)`, and related summaries.

- Illustrations saved in `/figures` (optional).

---

## 🛠️ Requirements

- Python 3.9+
- Libraries:

- `pandas`, `numpy`

- `matplotlib`, `seaborn`

- `scikit-learn`

### Local Installation
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
``
Eng . Yusha Al-Hussein
ISO 22000 and 9001 Systems Consultant
Food Safety and Quality 4.0 
