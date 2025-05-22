# Integrated Camber and Twist Morphing Wing for Unmanned-Aerial Vehicles

## 1. Introduction

Morphing wings represent a significant advancement in aircraft design, inspired by the adaptability seen in natural flyers like birds and insects. These wings change their shape during flight, enabling optimized performance across different flight conditions. This project explores a novel mechanism that integrates both **camber** and **twist morphing** to improve aerodynamic efficiency, maneuverability, and versatility.

The key motivation for this work is to replicate nature’s ability to adapt wing geometry dynamically, improving lift during takeoff and landing, reducing drag in cruise, and enhancing overall efficiency. Traditional aircraft designs rely on flaps and ailerons, which increase weight and mechanical complexity. Morphing mechanisms aim to minimize these components by embedding adaptability directly into the structure.

This project specifically targets an integrated design using two airfoils — **NACA0015** and **NACA6415** — with a morphing mechanism to transition between them. The rib-based design offers localized control of wing shape, and the prototype is fabricated using 3D printing technologies. The concept is experimentally validated through deformation tests and aerodynamic analyses.

---

## 2. Methodologies

### 2.1 Airfoil Selection

Two airfoils were selected:
- **NACA0015**: A symmetric airfoil offering low drag and predictable performance at moderate angles of attack.
- **NACA6415**: An asymmetric airfoil with high lift and improved lift-to-drag ratios, suitable for high-load or high-lift scenarios.

A rotational adjustment of 4° was applied to the NACA6415 to align maximum thickness with actuation mechanisms, enabling seamless transition from NACA0015 to NACA6415.

### 2.2 Aerodynamic Analysis

Airfoil performance was simulated in ANSYS Fluent under steady-state, pressure-based flow at 15 m/s and Reynolds number of 200,000. A C-type mesh domain was created, and simulations were conducted across a range of angles of attack.

The results confirmed that:
- **NACA0015** has the lowest drag at most AoA.
- **NACA6415** delivers higher lift throughout the AoA range.

### 2.3 Wing Configurations

Three main configurations were explored using rib-based camber control:
1. **Same airfoil at both ends** (NACA0015 or NACA6415)
2. **Different airfoils at root and tip**
3. **Morphing transition across span**

Preliminary analysis using XFOIL for a 1m span and 20cm chord wing showed the NACA6415 configuration generating the highest lift, while NACA0015 offered minimal drag.

### 2.4 Preliminary Design

#### Rib Mechanism

Each rib consists of:
- A **rigid center** section (housing actuators)
- A **thin trailing edge** with V-trusses for flexible skin shaping
- A **hinged leading edge**

Rods and actuators allow localized control over each rib’s shape, enabling multiple camber configurations along the span.

#### Materials Used

| Material | Density (kg/m³) | Young’s Modulus (MPa) | Yield Strength (MPa) | Poisson’s Ratio |
|---------|------------------|------------------------|-----------------------|------------------|
| PLA     | 1240             | 3292                   | 59                    | 0.33             |
| TPU     | 1450             | 2580                   | 63.6                  | 0.38             |

- **PLA** is used for the rigid and trailing edge components.
- **TPU** is selected for the leading edge due to its flexibility.

#### Structural Analysis

- Load: 1.5N applied to the trailing edge
- Max stress: 24 MPa (Factor of Safety > 2)
- Max deformation: 20.41 mm at trailing edge tip
- Deformed profile aligns closely with NACA6415

### 2.5 Prototype Testing

The rib structure was 3D printed using PLA and TPU and assembled to validate the mechanism.

- Rigid portion: PLA
- Trailing edge: PLA (1–2 mm thick plate for controlled bending)
- Leading edge: TPU (flexible and elastic)

### 2.6 Twist Morphing Concept

Two methods were proposed:
1. **Twisting a cylindrical spar** along the wing span
2. **Individually rotating ribs** about the spar axis

Both strategies aim to integrate twist without compromising camber control.

---

## 3. Tools Used

| Tool | Purpose |
|------|---------|
| **SolidWorks** | CAD modelling and assembly |
| **ANSYS Fluent** | Aerodynamic analysis of airfoils |
| **ANSYS Static Structural** | Structural stress and deformation evaluation |
| **XFOIL** | Preliminary aerodynamic performance of wing configurations |
| **3D Printer (PLA & TPU)** | Prototyping components |

---

## 4. Results and Future Scope

The camber morphing mechanism effectively transitioned between NACA0015 and NACA6415 airfoils. Simulation and experimental deformation data show close alignment:

| Part         | Computational Deformation | Experimental Deformation |
|--------------|---------------------------|---------------------------|
| Leading Edge | 5.9 mm                    | 7 mm                      |
| Trailing Edge| 20 mm                     | 23 mm                     |

Fatigue testing of 3D printed ribs is ongoing to assess long-term performance.

**Future Work Includes:**
- Full wing assembly with integrated spar and ribs
- Implementation of twist morphing mechanism
- Finalization of outer skin material with suitable flexibility and stiffness
- Integration into a UAV platform for field testing and real-flight validation

This project establishes a significant foundation for the development of adaptive, high-performance wings for next-generation aircraft.

