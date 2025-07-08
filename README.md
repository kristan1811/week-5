# week-5
**Capstone Project – Summer Analytics 2025**  
Hosted by: Consulting & Analytics Club × Pathway

---

##  Project Overview

Urban parking lots often face inefficiencies due to **static pricing** — leading to either **overcrowding** or **underutilization**. This project addresses that issue by developing a **dynamic, real-time pricing system** that adjusts parking rates based on actual demand signals and environmental conditions.

---

##  Objective

Build an intelligent pricing engine for 14 urban parking spaces that:

- Adjusts prices in real-time
- Accounts for:
  - Occupancy rate
  - Queue length
  - Traffic congestion
  - Special events
  - Vehicle type
  - Competitor pricing (optional)
- Starts from a base price of `$10`
- Ensures pricing is **smooth**, **bounded**, and **explainable**
- Optionally suggests **rerouting** vehicles to nearby lots

---

##  Dataset

- 73 days of data
- 14 parking lots
- 18 time points per day (every 30 mins from 8:00 AM to 4:30 PM)
- Features include:
  - Latitude/Longitude
  - Capacity, Occupancy, Queue length
  - Traffic level
  - Special day indicator
  - Vehicle type (car/bike/truck)

---

##  Model Architecture

Three incremental models were built from scratch using `numpy`, `pandas`, and `Pathway`:

1. **Baseline Linear Model**  
   Price increases linearly with occupancy rate.

2. **Demand-Based Pricing**  
   A weighted demand score is calculated using:
   - Occupancy
   - Queue length
   - Traffic level
   - Event flag
   - Vehicle type weight

3. **Competitive Pricing (Optional)**  
   - Uses geolocation to identify nearby lots
   - Adjusts pricing based on surrounding lot prices and availability
   - Can suggest rerouting vehicles

---

##  Tech Stack

- **Language**: Python
- **Libraries**: `numpy`, `pandas`, `Pathway`, `Bokeh`
- **Simulation**: Pathway (real-time streaming)
- **Visualization**: Bokeh (interactive pricing plots)
- **Execution**: Google Colab (required environment)

---

##  Visualizations

- Real-time pricing trends using **Bokeh**
- Comparative pricing vs. competitors
- Occupancy and queue heatmaps (optional)

---

##  Deliverables

- 🧾 Well-documented Colab notebook with pricing logic
- 📈 Real-time pricing dashboard
- 📄 Report explaining models, assumptions, and logic

---

>  **Goal**: Build a smart pricing engine that balances revenue, fairness, and availability using live data — simulating real-world urban parking dynamics.


> ## ✅ Tech Stack Used

| Layer              | Tools / Libraries Used                                                                 |
|--------------------|----------------------------------------------------------------------------------------|
| Programming Language | Python (with only numpy, pandas, and Pathway allowed by the rules)             |
| Data Ingestion      | Pathway (for streaming, real-time simulation)                                         |
| Data Handling       | pandas, numpy                                                                      |
| Modeling            | Custom implementation using NumPy/Pandas (linear/demand models from scratch)         |
| Visualization       | Bokeh (for real-time pricing graphs, occupancy trends)                                |
| Deployment/Sim      | Google Colab + Pathway Streaming Framework                                            |
| Geospatial Logic    | Haversine Distance (using lat-long for competitor proximity analysis)                |


---

## 🔄 Workflow Overview

1. **Data Simulation**
   - Simulated real-time data is generated using `Pathway` from `dataset.csv`.

2. **Ingestion**
   - Pathway processes the data stream chronologically, preserving timestamps and ensuring live behavior.

3. **Feature Engineering**
   - Extract key features per lot and time interval:
     - `Occupancy Rate = Occupancy / Capacity`
     - Queue Length
     - Traffic Congestion Level
     - Special Event Indicator
     - Encoded Vehicle Type
     - Competitor Prices (Model 3)

4. **Pricing Engine**
   - **Model 1: Linear**
     - Increases price proportionally with occupancy.
   - **Model 2: Demand-Based**
     - Computes a weighted demand score using multiple features.
     - Adjusts price based on normalized demand.
   - **Model 3: Competitive (Optional)**
     - Uses Haversine distance to find nearby lots.
     - Adjusts price considering nearby availability and rates.

5. **Real-Time Output**
   - Updated prices are emitted continuously and logged.
   - Optional rerouting decisions suggested for full lots.

6. **Visualization**
   - Real-time visualizations with **Bokeh**:
     - Price trends per lot
     - Demand vs. time
     - Competitor comparisons (if applicable)

---

> .




