# Design and Implementation of a PID Controller for a DC Motor

---

**Course**          : Control Systems / Open-Ended Lab  
**Lab Name**        : Design and Implementation of a PID Controller for a DC Motor  
**Student**         : Sumaira Safeer  
**Registration No** : FA22-BCE-019  
**University**      : COMSATS University Islamabad, Attock Campus  
**Department**      : Computer Engineering  

---

## 1. Project Overview

This open-ended lab focuses on the design, simulation, and analysis of a **Proportional-Integral-Derivative (PID) Controller** for a DC Motor using MATLAB and Simulink.

### Performance Objectives
- Rise Time < 1 second  
- Overshoot < 5%  
- Steady-State Error ≈ 0  

---

## 2. System Modeling

### Electrical Equation

$$
V(t) = R_a I_a(t) + L_a \frac{dI_a(t)}{dt} + E_b(t)
$$

Where:
$$
- \( V(t) \) = Applied armature voltage  
- \( I_a(t) \) = Armature current  
- \( R_a \) = Armature resistance  
- \( L_a \) = Armature inductance  
- \( E_b(t) = K_b \omega(t) \) = Back EMF  
$$
### Mechanical Equation

$$
K_t I_a(t) = J \frac{d\omega(t)}{dt} + B \omega(t)
$$

Where: 
$$
- \( K_t \) = Torque constant  
- \( J \) = Moment of inertia  
- \( B \) = Viscous friction coefficient  
- \( \omega(t) \) = Angular velocity  

$$

### Transfer Function (Simplified – neglecting \( L_a \))
$$
G(s) = \frac{\omega(s)}{V(s)} = \frac{K_t}{R_a (Js + B) + K_t K_b}
$$

### Assumed Motor Parameters

| Parameter | Value                  |
|-----------|------------------------|
| Ra        | 1 Ω                    |
| J         | 0.01 kg·m²             |
| B         | 0.1 N·m·s              |
| Kt        | 0.05 N·m/A             |
| Kb        | 0.05 V·s/rad           |

---

## 3. Controller Design

The PID controller is given by:

\[
C(s) = K_p + \frac{K_i}{s} + K_d s
\]

- Tuned using MATLAB `pidtune` with 60° phase margin  
- Manual fine-tuning applied for better performance  
- Target response time: 0.5 s  

---

## 4. Performance Results
| Metric               | Achieved Value | Requirement     | Status    |
|----------------------|----------------|-----------------|-----------|
| Rise Time            | 0.405 s        | < 1 s           | Achieved  |
| Overshoot            | 2.07%          | < 5%            | Achieved  |
| Settling Time        | 0.923 s        | < 3–4 s         | Achieved  |
| Steady-State Error   | ≈ 0            | ≈ 0             | Achieved  |

---

## 5. Tools Used

- MATLAB  
- Simulink  
- Control System Toolbox (`pidtune`, `stepinfo`, Bode, Nyquist, Root Locus)

---

## 6. Repository Structure

PID_Controller_DC_Motor_Control_Lab/

├── README.md

├── Report/

│   └── PID_Controller_DC_Motor_Lab_Report.pdf

└── MATLAB/

└── pid_dc_motor.m


---

## 7. How to Run
1. Open MATLAB  
2. Run the file `pid_dc_motor.m`  
3. The script will design the PID controller, simulate the step response, and generate performance metrics and plots.

---

## 8. Conclusion
A PID controller was successfully designed and implemented for a DC motor system. The controller met all required performance specifications (rise time, overshoot, and steady-state error). Time-domain and frequency-domain analyses confirmed the stability and robustness of the closed-loop system.

---

## 9. Prepared By
**Sumaira Safeer**  
FA22-BCE-019  
BS Computer Engineering  
COMSATS University Islamabad, Attock Campus  

---

**Disclaimer**: This lab report is prepared for academic purposes.
