# 🚗 Dynamic Pricing for Urban Parking Lots

**Capstone Project | Summer Analytics 2025**
Hosted by *Consulting & Analytics Club × Pathway*

---

## 🧠 Background & Motivation

Urban parking spaces are a scarce and high-demand resource. Static pricing fails to adapt to real-time conditions, leading to **overcrowding** or **underutilization**.

To address this inefficiency, we aim to build an intelligent **dynamic pricing engine** that:

* Updates parking rates based on real-time demand
* Utilizes ML models built **from scratch** using only `numpy`, `pandas`
* Ingests data in real time using **Pathway**
* Visualizes pricing trends using **Bokeh**

---

## 🗃️ Dataset Overview

**Duration:** 73 days
**Time Steps per Day:** 18 (every 30 minutes from 8:00 AM to 4:30 PM)
**Parking Lots:** 14 different locations

### Each time step includes:

#### 📍 Location Info:

* Latitude & Longitude (for proximity-based competition)

#### 🅿️ Parking Lot Features:

* Capacity (max vehicles)
* Occupancy (current vehicles parked)
* Queue Length (vehicles waiting)

#### 🚘 Vehicle Information:

* Type of incoming vehicle: `Car`, `Bike`, or `Truck`

#### 🌐 Environmental Features:

* Nearby Traffic Congestion
* Special Day Indicator (holidays/events)

---

## 🎯 Objective

Design a dynamic pricing engine for each parking lot that:

* Starts with a **base price of \$10**
* Adjusts prices **smoothly and realistically**
* Incorporates:

  * Historical occupancy trends
  * Queue lengths
  * Traffic conditions
  * Vehicle type
  * Special events
  * Competitor prices (optional)
* **(Optional)** Suggests rerouting to nearby lots when full

---

## ⚙️ Model Pipeline

We implement 3 models of increasing sophistication:

---

### 🔹 Model 1: Baseline Linear Model

A reference linear model adjusting price with occupancy rate.

**Formula:**

```math
Price_{t+1} = Price_t + α × (Occupancy / Capacity)
```

---

### 🔸 Model 2: Demand-Based Model

Incorporates multiple features to compute demand, then adjusts price.

**Example Demand Function:**

```math
Demand = α × (Occupancy / Capacity) + β × QueueLength − γ × Traffic + δ × IsSpecialDay + ε × VehicleTypeWeight
```

**Price Formula:**

```math
Price_t = BasePrice × (1 + λ × NormalizedDemand)
```

* Normalize demand
* Keep price within bounds: `0.5x` to `2x` of base price
* Smooth transitions — avoid erratic jumps

---

### 🔺 Model 3: Competitive Pricing (Optional Bonus)

Adds **location-based intelligence** and **competitor awareness**.

**Enhancements:**

* Compute distances using lat-long
* Compare with nearby lot prices
* Adjust price or reroute vehicles accordingly

**Strategies:**

* If **full** and nearby lots are **cheaper** → reduce price / suggest rerouting
* If nearby lots are **costlier** → raise your price reasonably

---

## 🧩 Tools & Libraries

* **Python (Colab)**: Implementation
* **Pandas, Numpy**: Data wrangling and model logic
* **Pathway**: Real-time data streaming and ingestion
* **Bokeh**: Real-time visualizations

---

## 📈 Visualization Requirements

Using **Bokeh**, provide:

* Real-time line plots for each parking lot's pricing
* Visual comparisons with nearby competitors
* Optional: Occupancy and queue visualizations

---

## 📝 Submission Checklist

* **Google Colab notebook**

  * Well-commented code
  * All 3 models implemented
* **Report/README**

  * Demand function explanation
  * Pricing assumptions
  * Model transitions and justifications
* **Visualizations**

  * Bokeh-based, embedded in notebook
* **Smooth and bounded pricing changes**

---

## 🔗 Useful Resources

* [Pathway – From Jupyter to Deploy](https://pathway.com/developers/user-guide/deployment/from-jupyter-to-deploy/)
* [Pathway – First Real-Time App](https://pathway.com/developers/user-guide/introduction/first_realtime_app_with_pathway/)
* [Summer Analytics 2025 Portal](https://www.caciitg.com/sa/course25/)

---

## 💡 Notes

* All modeling must be done **from scratch** (no sklearn, TensorFlow, etc.)
* Focus on **explainability** and **economic sense**
* Feel free to explore non-linear pricing or time-dependent functions (e.g., peak hours)

---

## 👨‍💻 Author

*Participant of Summer Analytics 2025*

> “Smart pricing isn’t just about numbers — it’s about understanding behavior.”

---

