# Fluid-Structure Interaction of Flexible beams using Smoothed-Particle Hydrodynamics

## 1. Introduction

The combination of high slenderness fibers and hyper-elastic materials presents an intriguing avenue of research with promising applications in various domains. High slenderness fibers, recognized by their exceptional length-to-diameter ratios, offer unique mechanical properties such as high tensile strength and low density. In parallel, hyper-elastic materials can undergo significant deformations and return to their original shape upon stress removal.

This synergy between high slenderness fibers and hyper-elastic materials has the potential to enhance stiffness, durability, and energy absorption capabilities—especially under dynamic and challenging conditions.

The motivation behind this study originates from experimental observations in fluid dynamics, particularly the analysis of “hairy flap” coatings used to control vortex shedding behind an immersed cylinder. This served as a foundation to understand the interaction between flexible materials and fluid flows. While individual immersed fibers may have a modest influence on the surrounding flow, their collective interaction plays a critical role in altering vorticity and global flow characteristics. This understanding is applicable to natural environments such as terrestrial canopies and submerged vegetation.

This project utilizes DualSPHysics, an open-source CFD solver based on the Smoothed Particle Hydrodynamics (SPH) method. SPH is a Lagrangian-based meshless technique well-suited for problems involving large deformations and moving boundaries. It allows accurate modeling of fluid-structure interaction (FSI) without the need for constant remeshing.

The primary objective of this project is to use SPH to analyze the FSI behavior of a flexible beam immersed in fluid, with the goal of validating the simulation model against mortar finite element method (FEM) results and exploring how varying the beam’s material properties influences the behavior.

---

## 2. Methodology

### Case Setup

The simulation was conducted within a 2D fluid channel, specifically designed for evaluating slender fiber deformation under high particle density conditions.

- [Geometric representation of fluid channel, CAD model representation]

The fluid properties were configured to replicate water with:
- Density (ρ): 1 g/cm³
- Viscosity: 0.004

An inter-particle distance of 0.006 cm was chosen. All surfaces, except inflow and outflow regions, were modeled as rigid boundaries.

A parabolic inflow velocity profile, both spatially dependent (on channel height) and temporally oscillating, was applied to mimic real-world wave-like flow behavior.

- [Parabolic inflow fluid profile, velocity-time variation]

The flexible beam was defined using the “flexstruc” library with the following material properties:

- [Table of properties of flexible beam]

### DualSPHysics Setup

The DualSPHysics configuration file included definitions of:
- Fluid and boundary properties
- Inflow and outflow profiles
- Time-stepping and simulation parameters

- [File setup description]

### Validation

The SPH model was validated against mortar FEM results by configuring both simulations with identical parameters. The SPH simulation was run for 0.075 seconds, capturing output at various time steps for comparison.

- [Initial configuration, fluid velocity in the fluid channel]
- [SPH and mortar FEM comparison]

Tip velocity and displacement were plotted across the time domain:

- [Tip velocity, displacement vs time]

### Convergence Study

To assess the reliability of the SPH model, a convergence study was conducted by varying the inter-particle distance. Key metrics such as maximum tip displacement were analyzed across simulations.

- [Table of comparison of convergence study, graph comparison]

The results were plotted with maximum tip displacement versus number of particles. Displacement values showed stability for inter-particle distances below 0.006 cm.

### Study of Various Parameters

A systematic analysis was conducted by varying the Young's modulus of the beam while keeping other properties constant. Simulations were performed for three values of Young’s modulus:  
- E₁ = 1×10⁶ Pa  
- E₂ = 5×10⁶ Pa  
- E₃ = 1×10⁷ Pa

- [Flow field visualization for different E]

For each case, flow field visualizations were captured at maximum fluid velocity (50 cm/s), where the beam was maximally deformed:

- [Flow field visualization at max velocity]

Additional visualizations were taken when fluid inlet velocity was zero, showing the beam returning to its original shape:

- [Flow field visualization at zero velocity]

The tip displacement results for all three cases were compared:

- [Comparison of tip displacement]

Beams with higher Young’s modulus (e.g., E = 1×10⁷ Pa) showed lower deformation, confirming the expected trend.

---


## 3. Tools Used

- FreeCAD  
- DualSPHysics

---

## 4. Results

The SPH model was successfully validated with mortar FEM results, proving its accuracy for simulating flexible structures in fluid domains. Variations in beam properties provided insights into tip behavior, deformation trends, and fluid interaction.

In future work, geometry parameters such as beam dimensions or fluid profile can be varied. Additionally, group behavior of multiple beams can be studied to assess their collective effect on fluid dynamics. These findings have strong potential in offshore structures, marine environments, and flexible component design for fluid-based systems.

