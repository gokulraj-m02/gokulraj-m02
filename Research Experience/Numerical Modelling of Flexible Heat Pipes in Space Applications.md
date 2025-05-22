# Numerical Modelling of Flexible Heat Pipes in Space Applications

## 1. Introduction

Heat pipes are pivotal in high-efficiency heat transmission applications, especially where compactness is vital, such as in space environments. These devices are essentially sealed tubes with interior surfaces lined with a porous capillary wick, utilising the phase change phenomenon and capillary action to transport heat effectively. 

This research focuses on the numerical modelling and experimental validation of **flexible heat pipes**, aiming to optimise their performance under various operational conditions and geometric configurations.

In space applications, thermal management is critical to ensure the functionality and longevity of onboard systems and instruments. Traditional rigid heat pipes are commonly used for effective heat transfer in satellites and spacecraft. However, the evolving complexity of spacecraft designs and the need for efficient space utilisation call for more adaptable systems. **Flexible heat pipes** offer enhanced configurability and integration flexibility, especially in confined and variable environments.

**Objective:**  
Develop a robust numerical model to simulate and analyse the thermal performance of flexible heat pipes specifically for space applications, optimising the design under space-constrained conditions.

---

## 2. Methodologies

### ➤ Experimental Analysis

The experimental apparatus consists of:

- **Thermosyphon tube**: Stainless steel
- **Heating and cooling blocks**: Aluminium
- **Adiabatic (flexible) portion**: Thin-walled corrugated structure covered with steel braids
- **Working fluid**: 18.7 ml of deionised water (30% filling ratio)
- **Input power**: 25W to 250W (DC power source)
- **Cooling method**: Cooled water circulation in condenser
- **Measurements**: Thermocouples placed along the length for temperature distribution

**Bending Angles Tested:**  
0°, 30°, 60°, 90°

**Results:**

- Temperature distribution is recorded along the setup.
- Effective thermal conductivity is calculated.
- Increasing bending angle reduces effective thermal conductivity.

**Figures:**  
- [Experimental apparatus schematic]  
- [Bending angle diagrams]  
- [Temperature vs thermocouple position plot]  
- [Thermal conductivity vs input power plot]

---

### ➤ Numerical Analysis

The numerical study begins with the simulation of **boiling and condensation** in a thermosyphon using **ANSYS FLUENT**, validated against experimental data. The research expands to include:

- **Straight heat pipes with wick structures**
- **Pipe bending angles**: 0°, 30°, 60°, 90°
- **Water fill ratios**: 10%, 30%, 50%
- **Power input range**: 25W to 250W

**Simulation Framework:**

- **Software**: ANSYS SpaceClaim, FLUENT
- **Physics models**: Volume of Fluid (VOF), Lee model for mass transfer
- **Flow modelling**: Multiphase flow, steady-state, pressure-based solver

#### Methodology Breakdown

1. **Boiling and Condensation Simulation (Thermosyphon)**  
   - Geometry: 720 mm length, 12.7 mm OD, 10.5 mm ID  
   - Meshing: Polyhedral cells, boundary layer refinement  
   - Grid independence test: Mesh with 1.04M cells chosen  
   - Boundary conditions: Deionised water, stainless steel, VOF model  
   - Initialisation: 333K, 20,000 Pa, 30% infill (patched)  
   - Iterations: 10,000  

   **Figures:**  
   - [Meshed geometry]  
   - [Grid independence table]  
   - [Boundary condition table]  
   - [Temperature, pressure, VOF contours]  

2. **Porous Media Analysis**  
   - Geometry: Three concentric cylinders (solid shell, porous zone, fluid zone)  
   - No inlet/outlet (patched 30% infill)  
   - Streamlines show evaporation-condensation and return through porous media  

   **Figures:**  
   - [Geometry cross-section]  
   - [Boundary condition table]  
   - [Phase velocity streamline plot]  

3. **Full Heat Pipe Analysis (Coupled Physics with Wick)**  
   - Geometry: CAD model with different bend angles (0° to 90°)  
   - Total length: 720 mm; OD: 12.7 mm; ID: 10.5 mm  
   - Wick thickness: 1 mm  
   - Meshing: Half symmetry model, polyhedral mesh  
   - Grid independence test: Final mesh with 4.6 lakh cells  
   - No gravity (g = 0 m/s² for space simulation)  
   - Boundary simplification: Cooling simulated as convection  
   - Iterations: 5,000  
   - Initialisation: 333K, 20,000 Pa, 50% patched  

   **Figures:**  
   - [CAD models at different angles]  
   - [Meshing of 90° pipe]  
   - [Volume fraction contour]  
   - [Temperature and pressure contours]  
   - [Thermal conductivity vs bending angle plot]  

---

## 3. My Role

- Designed the experimental setup and conducted all thermal performance tests.
- Developed all numerical models using ANSYS Fluent and SpaceClaim.
- Performed meshing, simulation runs, and result validation.
- Conducted post-processing and plotted results for comparative analysis.
- Ensured consistency between experimental and numerical results.
- Automated data processing pipelines for temperature analysis and thermal conductivity estimation.

---

## 4. Tools Used

| Tool | Purpose |
|------|---------|
| **SolidWorks** | CAD modelling of heat pipe geometries |
| **ANSYS Design Modeller / SpaceClaim** | Geometry creation for simulation |
| **ANSYS Fluent** | Multiphase simulation of heat transfer |
| **Excel / Python** | Data processing, result plotting |

---

## 5. Results

- A robust numerical model was developed to simulate boiling, condensation, and porous media effects in flexible heat pipes.
- The model accurately matched the experimental results for temperature distribution and thermal conductivity.
- Effective thermal conductivity decreases with increasing bending angle, both experimentally and numerically.
- The modular simulation strategy allowed for isolated testing of individual phenomena, improving model reliability.

**Future Scope:**

- Extend simulations to dynamic boundary conditions (e.g., pulsed heat input).
- Optimise wick structure geometry for enhanced capillary action.
- Apply machine learning for real-time thermal control and predictive modelling in satellites.

---
