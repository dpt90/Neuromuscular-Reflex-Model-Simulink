# Neuromuscular-Reflex-Model-Simulink


## **1. Introduction**

This project investigates the **step responses of a neuromuscular reflex model** for different values of the feedback gain parameter **β (beta)** using **MATLAB/Simulink**.
Neuromuscular reflex dynamics provide valuable insight into the behavior of patients with neurological disorders and help in understanding the biomechanical and control characteristics of the human forearm under sudden load disturbances.

The model simulates a controlled experiment in which a subject supports a weight with the forearm while the arm is constrained to move only in the vertical plane. At time *t = 0*, an additional weight is suddenly released onto the arm, and the angular motion is recorded.
Different β values (50, 100, and 150) are analyzed to observe their influence on system behavior.

---

## **2. Experimental Description**

The neuromuscular model considers the following controlled test:

* The subject sits comfortably, with shoulder and elbow supported so the upper arm remains horizontal.
* The forearm is allowed to move only vertically.
* The wrist is connected to a cord running over a pulley to support a weight.
* The forearm begins at an initial angle of **135°**.
* No specific instructions are given to the subject except to relax while holding the weight.
* At **t = 0**, an electromagnetic catch is released, increasing the load abruptly.
* The angular displacement **θ(t)** of the forearm is measured during and after the sudden weight release.

---

## **3. Neuromuscular Reflex Model**

The system block diagram represents:

* Mechanical dynamics of the forearm
* Feedback loop involving neuromuscular response
* Gain parameter **β** controlling reflex strength
* Transmission and delay elements

The system transfer function is given by:

---



## **System Transfer Function**

The system transfer function for the neuromuscular reflex model is given by:

```
θ(s) = 1 / [ (BJ/k)·s² + J·s + B ]
```

---

## **Given Parameters**

* `J = 0.1   kg·m²`
* `k = 50    N·m`
* `B = 2     N·m·s`
* `T_d = 0.02   s`
* `τ = 1/300    s`
* `r = 1/300    s`
* `η = 5`

---

## **Substitution**

First compute the coefficient:

```
BJ/k = (2 × 0.1) / 50
     = 0.2 / 50
     = 0.004
```

Thus, the transfer function becomes:

```
H(s) = θ(s) = 1 / (0.004·s² + 0.1·s + 2)
```

---

## **4. Simulink Model**

The Simulink model includes:

* Transfer function blocks for system dynamics
* Delay elements
* Feedback loop incorporating β
* Three parallel branches for β = **50, 100, 150**
* Scope to observe all responses simultaneously

A single unified model is used to compare behavior for various β values.

---

## **5. Simulation Results**

### **Model Response for β = 50, 100, 150**

The system output **θ(t)** exhibits different characteristics depending on the feedback gain:

### **For β = 150**

* Response becomes **damped oscillatory**
* Final steady-state value is **smaller**
* Reflects higher feedback strength and disturbance attenuation

### **For β = 100 (Nominal Value)**

* Balanced response
* Moderate transient oscillations
* Stable final angular value

### **For β = 50**

* System becomes **overdamped**
* No oscillation
* Final output angle is **larger** compared to β = 100 and 150

### **Interpretation**

Higher feedback gain (β):

* Improves disturbance rejection
* Reduces steady-state error
* Increases oscillatory nature of response

Lower feedback gain (β):

* Produces slower, overdamped behavior
* Results in higher final angle due to insufficient correction

---

## **6. Conclusion**

The step response analysis of the neuromuscular reflex model demonstrates that the **feedback gain β plays a critical role** in shaping system behavior.
Larger β values improve disturbance handling but increase oscillations, while smaller β values yield overdamped, slower responses with larger final displacement.

Thus, the effects of β on neuromuscular reflex dynamics have been successfully studied using SIMULINK.

---

## **7. Repository Contents**

```
📁 Neuromuscular-Reflex-Distributed-Model
│
├── models/
│   └── simulink_model.slx
│
├── figures/
│   ├── block_diagram.png
│   ├── transfer_function.png
│   ├── step_responses.png
│
├── documentation/
│   └── project_report.pdf
│
└── README.md   ← (This file)
```

---

## **8. How to Run the Simulation**

### **Requirements**

* MATLAB (R2020 or later recommended)
* Simulink
* Control System Toolbox (optional but useful)

### **Steps**

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/Neuromuscular-Reflex-Distributed-Model.git
   ```
2. Open MATLAB and navigate to the project directory.
3. Open the Simulink file:

   ```matlab
   open('simulink_model.slx');
   ```
4. Set β values in the model (50, 100, 150).
5. Run the simulation.
6. View results in the scope window.

---

