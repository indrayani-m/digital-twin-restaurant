# 🍽️ Restaurant Digital Twin for Food Inventory & Waste Management  
### ACM Winter School 2025 – Engineering the Future with Digital Twins in association with RBU Nagpur, VNIT Nagpur and Persistent Systems, Nagpur

## 📌 Overview

This project presents a **Digital Twin Model** of a restaurant system using **System Dynamics - Stock and Flow Modelling (Vensim)** to analyze:

* Food preparation vs consumption
* Inventory behavior over time
* Food wastage (spoilage + leftovers)

---

## 🧠 System Model

![System Diagram](images/system_diagram.png)

---

## 🧩 Key Components

### 🟦 Stocks

* **Food Inventory (kg)**
* **Leftover Food (kg)**
* **Cumulative Waste (kg)**

---

### 🔄 Flows

| Flow                  | Description                       |
| --------------------- | --------------------------------- |
| Food Preparation Rate | Incoming prepared food            |
| Consumption Rate      | Food consumed by customers        |
| Food Spoiled          | Waste due to storage & shelf life |
| Leftover Generated    | Excess food after demand          |
| Leftover Disposed     | Waste disposal flow               |

---

## ⚙️ Important Equations

### 🟢 Food Inventory

```
INTEG(
 food preparation rate+leftover generated-consumption rate-food spoiled,
 0
)
```

---

### 🟢 Food Preparation Rate

```
MAX(0,
 MIN(expected demand * weight per plate * market influence * menu mix planning,
     base preparation rate * festival factor * day factor(Time)))
```

---

### 🟢 Leftover Generated

```
MAX(0, food preparation rate - consumption rate)
```

---

### 🟢 Leftover Disposed

```
Leftover food/disposal time
```

---

### 🟢 Food Spoiled

```
Food Inventory * storage condition * spoilage rate
```

---

## 📊 Inputs & Multipliers

| Variable                     | Value | Unit        |
| ---------------------------- | ----- | ----------- |
| Base Preparation Rate        | 200   | kg/day      |
| Festival Factor              | 1.5   | dmnl        |
| Avg Consumption per Customer | 0.5   | kg/customer |
| Consumption Time             | 1     | day         |
| Disposal Time                | 1     | day         |

---

## 📈 Dynamic Inputs (Lookup Functions)

* Online Orders Forecast
* Reservation Count
* Customer Review Trends
* Competitor Activity

(All modeled using **WITH LOOKUP(Time)**)

---

## 🎯 Objective

To simulate:

* Inventory stability
* Demand fluctuations
* Waste generation

and help optimize:

* Food preparation decisions
* Waste reduction strategies

---

## 🛠️ Tools Used

* Vensim (System Dynamics)
* Modeling & Simulation

---

## ⚠️ Units Consistency & Model Warnings

During simulation in Vensim, the following unit consistency warnings were observed:
Warning: units in equation for - competitor activity
Lookup -#competitor activity#- used with dimensioned argument Day

Warning: units in equation for - consumption rate
Lookup -number of customers- used with dimensioned argument Day

Warning: units in equation for - consumption rate
Lookup -peak hours- used with dimensioned argument Day

Warning: units in equation for - customer review trends
Lookup -#customer review trends#- used with dimensioned argument Day

Warning: units in equation for - food preparation rate
Lookup -day factor- used with dimensioned argument Day

Warning: units in equation for - online orders forecast
Lookup -#online orders forecast#- used with dimensioned argument Day

Warning: units in equation for - reservation count
Lookup -#reservation count#- used with dimensioned argument Day


### 🧠 Interpretation
These warnings occur because `WITH LOOKUP(Time)` uses Time (Day) instead of dimensionless input.

### ✅ Conclusion
The model behavior remains valid; warnings are due to unit strictness in Vensim.

---

## 🏆 Achievement

🏅 **Awarded "Top Performer"** for outstanding modeling and presentation  
among 50 participants, evaluated by **TCS experts** at ACM Winter School 2025.

---

## 👩‍💻 Author

Sanika Gadhave

Aditi Joshi

Indrayani Mude

Krish P. Gokhale

Zubiya Khan

---
