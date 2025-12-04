# Linear Kalman Filter IMU Smoothing
### EuRoC MAV (V1_01_easy) – 6D State-Space Filtering with FilterPy

This project applies a **6-dimensional linear Kalman Filter** to smooth noisy IMU
gyroscope and accelerometer measurements from the **EuRoC MAV** dataset
(`mav0/imu0/data.csv`).  
The goal is **state-space smoothing and estimation**

---

## Dataset
**Source:** EuRoC MAV – V1_01_easy  
**Signals used:**
- Gyroscope: `w_RS_S_x`, `w_RS_S_y`, `w_RS_S_z`
- Accelerometer: `a_RS_S_x`, `a_RS_S_y`, `a_RS_S_z`
- Timestamp converted from nanoseconds → seconds

---

## Model Summary
A simple 6D random-walk Kalman model:

- **State:**

$\displaystyle x_t = [\,\omega_x,\ \omega_y,\ \omega_z,\ a_x,\ a_y,\ a_z\,]^T$

- **Dynamics:**

$\displaystyle F = I_6,\qquad H = I_6$

- **Noise:**
    - `R` = empirical IMU variances
    - `Q` = small diagonal process noise (fraction of `R`)

Filtering is performed with **FilterPy**, followed by **RTS smoothing**.

---

## Notebook Contents
1. **EDA**
    - load IMU
    - plots of gyro & accel
    - noise characteristics
2. **Kalman Filter Implementation**
    - model setup (F, H, Q, R)
    - filtering + smoothing
3. **Diagnostics**
    - residuals
    - ACF
    - histograms
    - FFT (noise reduction)
    - variance reduction
    - innovation analysis
    - 1-step-ahead prediction
4. **Interpretation & conclusion**
    - TBD
---
