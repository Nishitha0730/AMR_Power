# 🚀 Industrial AMR Project - Power System Design

This repository documents the **power system design and implementation** for our industrial Autonomous Mobile Robot (AMR) project.  
The AMR is designed to carry a **5 kg payload** (total mass **25 kg**) and navigate autonomously using SLAM with a **Jetson Nano** and **LiDAR**.

---

## 🛠️ My Contribution

I primarily worked on:

- Selecting motors, drivers, and gearbox based on torque and speed requirements.
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
