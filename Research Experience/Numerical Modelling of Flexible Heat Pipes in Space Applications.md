# Numerical Modelling of Flexible Heat Pipes in Space Applications

## 1. Introduction

Heat pipes are pivotal in high-efficiency heat transmission applications, especially where compactness is vital, such as in space environments. These devices are essentially sealed tubes with interior surfaces lined with a porous capillary wick, utilising the phase change phenomenon and capillary action to transport heat effectively. 

This research focuses on the numerical modelling and experimental validation of **flexible heat pipes**, aiming to optimise their performance under various operational conditions and geometric configurations.

In space applications, thermal management is critical to ensure the functionality and longevity of onboard systems and instruments. Traditional rigid heat pipes are commonly used for effective heat transfer in satellites and spacecraft. However, the evolving complexity of spacecraft designs and the need for efficient space utilisation call for more adaptable systems. Flexible heat pipes offer enhanced configurability and integration flexibility, especially in confined and variable environments.

**Objective:**  
Develop a robust numerical model to simulate and analyse the thermal performance of flexible heat pipes specifically designed for space applications.

---

## 2. Methodologies

### 2.1 Experimental Analysis

The experimental setup consists of a thermosyphon tube, heating block, and cooling block. The heating and cooling blocks are made of aluminium, while the thermosyphon tube is made of stainless steel. The adiabatic (flexible) portion has a thin-walled corrugated structure and is covered by steel braids. 

Heat input to the evaporator section is provided through a DC power source, ranging from 25W to 250W in increments of 25W. In the condenser section, cooled water is circulated to absorb the heat effectively. The system operates with a 30% filling ratio of the working fluid, which corresponds to 18.7 ml of deionised water. The thermocouples were placed along the length of the thermosyphon to record the temperature distribution across its surface.

> [Experimental apparatus, schematic sketch of experimental]

To examine the effect of bending on thermal performance, the experiments were carried out at four distinct bending angles: 0°, 30°, 60°, and 90°. At each angle, temperature readings were recorded at different power inputs, and the effective thermal conductivity was calculated using the temperature differential between the evaporator and condenser sections.

> [Bending angle of the pipes]

Temperature readings along the surface, from the evaporator to the condenser, were plotted to understand temperature distribution and heat transfer behaviour. These data points allowed for evaluating how bending affects thermal conductivity under varying operational conditions.

> [Temp vs thermocouple position]

The calculated thermal conductivity was then plotted against input power for each bending angle. The results consistently showed a decrease in effective thermal conductivity with increasing bending angles, indicating the thermal resistance introduced due to geometrical changes.

> [Thermal conductivity vs input power]

---

### 2.2 Numerical Analysis

The numerical study begins with simulating boiling and condensation processes in a thermosyphon system with deionised water. This is initially validated with empirical data to ensure accuracy. The simulation is later extended to include straight heat pipes with wicks to capture the combined effect of phase change and capillary action. To examine performance under deformation, simulations are performed at different bending angles (0°, 30°, 60°, 90°) and water fill ratios (10%, 30%, and 50%) with heat inputs ranging from 25W to 250W.

All simulations are conducted using ANSYS Fluent with multiphase modeling (Volume of Fluid approach) and Lee model for mass transfer. The analysis is conducted in three phases: thermosyphon modeling, porous media modeling, and a combined simulation of both phenomena.

---

#### 2.2.1 Thermosyphon Analysis

A three-dimensional numerical model of the thermosyphon is created in ANSYS SpaceClaim. The geometry consists of a 720 mm long tube with a 12.7 mm outer diameter and a 10.5 mm inner diameter. The geometry is divided into three zones: the evaporator (heat input), the adiabatic section (no heat transfer), and the condenser (convective cooling applied).

> [Schematics geometry]

Meshing is performed with a fine surface mesh of 0.2 mm minimum element size and 10 boundary layers is applied to the evaporator, adiabatic section, condenser, and walls to capture the near-wall effects. The internal volume is filled with polyhedral elements up to a maximum size of 0.5 mm, to achieve a balance between accuracy and efficiency.

> [Meshed geometry]

A grid independence study is carried out by comparing results for mesh sizes ranging from 1 lakh to over 20 lakh cells. The mesh with 10,45,482 cells is selected for simulation, as it provides temperature results close to that of the finer mesh.

|No. of cells | 2,13,904 | 10,45,482 | 20,86,861 |
|-------------|----------|-----------|-----------|
| T_evap,avg | 353.981 K | 350.824 K | 350.427 K |
| T_adia,avg | 344.872 K | 341.785 K | 341.232 K |
| T_cond,avg | 335.137 K | 334.648 K | 334.224 K |

*Table of independent results*

Material definitions include stainless steel for the solid regions and deionised water (liquid and vapour phases) for the working fluid. The simulation uses a pressure-based solver with gravity enabled along the length and operates in steady state. The VOF model is used to track the liquid-vapour interface, where water vapour is set as the primary phase and water liquid (deionized water) as the secondary.

| Boundary condition | Thermal BC type | Value |
|--------------------|-----------------|-------|
| Evaporator surface | Heat flux | 12531 Wm2 |
| Adiabatic surface | Heat flux | 0 |
| Condenser surface | Convection | 102 W/mK (F.S.T. - 303K)|
| Wall | Heat flux | 0 |
| Inner walls | Velocity | No slip |
| Symmetry wall | Symmetry | - |

*Table of boundary conditions* 

| Model | Settings |
|-------|----------|
| Energy equation | Enabled |
| Multiphase | VOF |
| Space | 3D |
|Time | Steady |
| Viscous | Standard k-e, Enhanced wall |

*Table of setup*

The setup is initialised with a temperature of 333K and pressure of 20,000 Pa. A 30% fill ratio is patched by assigning a liquid volume fraction of 1 in the liquid region and 0 in the vapour region.

> [Image of Initialised temperature, volume fraction]

The steady-state simulation of the thermosyphon was run for 10,000 iterations. The average temperature on the evaporator section and condenser section from the simulation closely follows the temperature values from the experimental data for the corresponding heat input. Thereforem a good agreement was observed between experimental and numerical analysis.

> [Evaporator, condenser, adiabatic VOF]  
> [Temperature contour, pressure contour]

---

#### 2.2.2 Porous Media Analysis

This model combines boiling and condensation with porous media interaction to observe the coupling between the two phenomena. The geometry consists of three concentric cylinders constructed using the experimental setup dimensions: an outer solid shell, a porous zone, and an inner fluid region. The solid region (outermost cylinder) is divided into evaporator region, adiabatic region and a condenser region in the same ratios as done in the boiling and condensation setup. The porous region sits between the shell region and the fluid region. The geometry mimics the cross-section of the heat pipe in all the three regions.

A polyhedral mesh is applied using ANSYS Fluent Meshing. The same materials are used from the thermosyphon case—deionised water (vapour and liquid) and stainless steel.

The simulation has no inlets or outlets. A 30% fill is patched similarly by assigning a liquid volume fraction of 1 in both fluid and porous regions.

> [Table of boundary conditions]  
> [Table of setup details]

The simulation is executed in steady-state for 5,000 iterations. Results confirm the operational principle of wick-based heat pipes: vapour travels from the evaporator to the condenser, condenses, and then returns via the porous medium to the evaporator.

> [VOF for vapour]

The visualisation shows where the blue streamlines ending at the condenser zone and transitioning into the porous region. Here, the red streamlines emerge, moving in the reverse direction toward the evaporator.
> [Streamline plot for phase velocity]

---

#### 2.2.3 Full Heat Pipe Analysis

The final simulation incorporates insights from both thermosyphon and porous media studies. The full model simulates the heat pipe as constructed experimentally, with boiling, condensation, and porous media effects. Also, it simulates the practical utilisation of heat pipes in space applications, where the gravitational force is negligible (g = 0 m/s²). Simulations are performed for bending angles of 0°, 30°, 60°, and 90° at a constant heat input of 100W.

In this final setup, the effect of cooling water is replaced by providing convection at the contact surface between the cold water and cooling block. A separate analysis was carried out to find the heat transfer coefficient at the cooling water contact surface. It is found that for different values of heat input to the cooling block at the centre and for various water inlet temperatures, the heat transfer coefficient at the contact surface remains constant and it is given as the boundary condition. In this way, the computational cost to simulate a water flow is reduced.

The geometry is modeled in SolidWorks and features a 720 mm length, 12.7 mm outer diameter, 10.5 mm inner diameter, and a 1 mm wick layer. Due to symmetry, only half the body is simulated to reduce computational load.

> [CAD model of the geometry at different angles]  
> [Meshing of 90 degree]

Grid independence is tested with meshes ranging from 1.78 lakh to 33.25 lakh cells. The mesh with 4.6 lakh cells is chosen due to its close agreement with the finest mesh.

> [Table of grid independence results]

Materials include stainless steel (adiabatic region - shell), deionised water (liquid and vapour phases), and aluminium (heating and cooling blocks).

> [Table of boundary conditions]

A Pressure-based solver, without gravity and operating under steady state conditions, is employed. The simulation setup and solver settings remain consistent with those utilised in previous simulations involving boiling and condensation, and porous medium. The setup is initialised with a saturation temperature of 333 K and a pressure of 20,000 Pa and the liquid region (50% of heat-pipe region) is patched with liquid volume fraction of 1.

> [Table for model details]
> [Volume fraction patch]

The simulation is run for 5,000 iterations. The following plots shows the area-weighted average of temperature of evaporator, condenser and adiabatic section. From these plots, it is observed that the numerical model for the experimental setup of the heat pipe is providing converging results which are reliable.

> [Average weighted temperatures of evaporator, condenser, adiabatic; volume fraction vs iterations]

In the following image, the red color shows the presence of only vapour (vapour volume fraction = 1) whereas, the blue region shows the presence of only liquid (vapour volume fraction = 0). In the enlarged view, the condensation of vapour into liquid in the porous zone is observed.
> [Volume fraction contour of entire setup]  
> [Temperature contour and pressure contour]

Similarly, the simulations for other bending angles of the heat pipe were conducted with same settings and temperature balues across the surface of the heat pipe is recorded. Then, the calculated thermal conductivity of the heat pipe is plotted versus bending angle. And it is observed that the thermal conductivity decreases gradually as the bending angle increases.

> [Thermal conductivity of heat pipe vs bending angle]

---

## 3. My Role

- Conducted experimental analysis on the thermosyphon setup, recording temperature data under various power inputs and bending angles.
- Calculated effective thermal conductivity based on experimental results and plotted performance metrics.
- Designed the geometry of the heat pipe model for numerical analysis and simulated for all four bending angles (0°, 30°, 60°, 90°) using ANSYS Fluent.
- Worked on a simplification approach to replace cooling water simulation by calculating and applying an equivalent heat transfer coefficient through separate simulations.


---

## 4. Tools Used

- SolidWorks
- Ansys DesignModeler
- Ansys Fluent

---

## 5. Results

- A numerical model was developed to simulate boiling, condensation, and porous media effects in flexible heat pipes.
- The model closely matched the experimental results for temperature distribution and thermal conductivity.
- Effective thermal conductivity decreases with increasing bending angle (observed both experimentally and numerically).
- The simulation was carried out in separate parts initially which made it easier to model the physical processes accurately and integrated later to ensure the model's reliability.

**Future Scope:**

- Extend simulations to dynamic boundary conditions (e.g., pulsed heat input).
- Conduct simulations with corrugated-structure in the flexible portion of the heat pipe.
- Optimise wick structure geometry for enhanced capillary action.

---
