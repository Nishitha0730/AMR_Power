# 🚀 Industrial AMR Project - Power System Design

This repository documents the **power system design and implementation** for our industrial Autonomous Mobile Robot (AMR) project.  
The AMR is designed to carry a **5 kg payload** (total mass **25 kg**) and navigate autonomously using SLAM with a **Jetson Nano** and **LiDAR**.

---

## 🛠️ My Contribution

I primarily worked on:

- Performing detailed **torque and power calculations**.
- Designing the complete **power distribution system**.
- Selecting and integrating DC-DC converters (boost & buck) to meet system demands.

---

## ⚙️ Motor & Motion System

| Component      | Model/Spec                      |
|----------------|--------------------------------|
| Motor          | 24HS40-5004D-E1000 (4.0 Nm Closed-loop Stepper) |
| Driver         | CL57T-V41                      |
| Gearbox        | EG24-G10                       |
| Wheel Diameter | 12.5 cm                          |
| Max Speed      | 0.6 m/s                        |
| Acceleration   | 0.6 m/s²                       |

---

## 📊 Torque & Power Calculations

### 🔩 Force & Torque
- **Rolling friction force:**  

F_friction = μ * M * g = 0.02 * 25 * 9.81 ≈ 4.9 N

- **Acceleration force:**
F_acceleration = M * a = 25 * 0.6 = 15 N

- **Torque at constant velocity:** 
Torque = (4.9 * 0.0625) / 2 ≈ 0.153 Nm


- **Torque during acceleration:**  
Torque = ( (15 + 4.9) * 0.0625 ) / 2 ≈ 0.62 Nm  



### ⚡ Electrical Power
| Component      | Voltage | Current | Power |
|----------------|---------|---------|-------|
| Motors         | 24 V    | 4 A     | 92 W  |
| LiDAR          | 5 V     | 0.5 A   | 2.5 W |
| Jetson Nano    | 5 V     | 2 A     | 10 W  |

- **Mapping operation:**  
Total current ≈ 6.5 A, Total power ≈ 105 W

- **Normal operation (~20% accel):**  
Total current ≈ 3.5 A, Total power ≈ 49 W




---

## 🔌 Power Distribution & Conversion

### ⚡ Power Distribution
We used a **Power Distribution Board (PDB) 60A XT30** to safely distribute power.

> [Power Distribution Board Product](https://techrolk.com/shop/product/power-distribution-board-pdb-60a-xt30-pre-soldered/)

### 🚀 DC-DC Converters
- **Boost converter** to power motors (22.2V → 36V).
- [Boost Converter](https://tronic.lk/product/dc-dc-boost-converter-10-32vdc-to-12-35vdc-10a-150w-adj)
- **Buck converter** to supply Jetson Nano & LiDAR (22.2V → 5V).
- [Buck Converter](https://tronic.lk/product/12a-100w-dc-to-dc-step-down-buck-adjustable-constant-vo)

---


## 🔋 Battery & BMS

### 🔥 Battery Pack
| Specification         | Value                     |
|------------------------|--------------------------|
| Type                   | Li-ion 6S (22.2V nominal) |
| Capacity               | 5 Ah                     |
| Max Discharge Current   | ~50 A (10C burst)        |

### 🧠 BMS: JK-JBD4A8S4P
| Feature                | Value                   |
|-------------------------|-------------------------|
| Cells Supported         | 4S–8S Li-ion/LiFePO4    |
| Max Charging Current    | Configurable, typical ~20 A |
| Balancing Current       | ~1.5 A active balancing |
| Communication           | UART/Bluetooth App     |

✅ **Functions:**  
- Cell balancing (during charging & standby)  
- Overcharge & overdischarge protection  
- Overcurrent & short circuit protection  
- Bluetooth app for live cell voltages, current, cycle data.

> 📖 [JK BMS Manual](https://www.jkbms.com)

---

## 🔌 Battery Charging Process

We used the **iMAX B6 Smart Balance Charger** for charging our 6S Li-ion battery safely.

### ⚠️ Safety Notes
- Select correct battery type.
- Always use **Balance Charge** mode.
- Never leave charging battery unattended.
- Use a fireproof charging bag if possible.

---

### 🪫 Charging Steps (with iMAX B6)

1. **Connect Battery and Balance Lead**  

2. **Power On Charger**  

3. **Select Li-ion Balance Mode**  
   Navigate: `Li-ion BATT` → `Li-ion BALANCE`  

4. **Set Parameters**  
   - Battery Type: Li-ion  
   - Cell Count: 6S  
   - Voltage: 21.6V  
   - Current: 0.5C (max)

5. **Start Charging**  
   - Hold `ENTER` to start.  
   - Confirm cell count and press again.  

6. **Monitor the Charging Process**  
   - Total voltage should reach < 25.2V  
   - Check individual cell voltages  
   ![Step 6](images/step6_monitor.jpg)
---

### 🔋 Charging Profile Summary

| Setting         | Value              |
|----------------|--------------------|
| Battery Type    | Li-ion (6S)        |
| Max Voltage     | 25.2 V             |
| Charge Current  | < 0.5 C             |
| Mode            | Li-ion Balance       |

---

## 📚 References & Calculations

- [Rolling friction (Engineering Toolbox)](https://www.engineeringtoolbox.com/rolling-friction-resistance-d_1303.html)
- [Stepper motor torque guide (Portescap)](https://www.portescap.com/en/newsroom/whitepapers/2023/08/a-guide-to-stepper-motor-terminology-and-parameters)
- [Voltage & current impact on stepper motors (Mechtex)](https://mechtex.com/blog/impact-of-voltage-and-current-on-stepper-motor-performance)

---

## 📝 Acknowledgments

This work was completed as part of a team project for building an **industrial-grade AMR with SLAM**.  
My primary responsibility was designing the **complete power system**, performing electrical & torque analysis, and integrating converters and distribution hardware.

---

## 📷 Future Work

✅ Add wiring diagrams & power schematics  
✅ Include BOM (Bill of Materials)  
✅ Upload photos of actual power setup on the robot  

---

## ✨ Thanks for checking out this project!

Feel free to fork, open issues, or contribute!
