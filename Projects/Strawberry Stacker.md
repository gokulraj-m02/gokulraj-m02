# Strawberry Stacker (E-Yantra Robotics Competition - IIT Bombay)

## 1. Introduction

This project was developed as part of the **E-Yantra Robotics Competition**, conducted by **IIT Bombay** during their annual Techfest. The problem statement is focused on automating the collection of strawberries from agricultural fields using drones.

The automation process involves:
- Identifying strawberry collection boxes with **Aruco markers**,
- Picking them up using a drone,
- Navigating through crop rows, and
- Depositing the boxes onto **color-coded drop zones (trucks)** based on their color.

This system aims to reduce the manual effort required for post-harvest tasks and improve efficiency.

---

## 2. Process & Methodologies

The project was executed through a step-by-step process involving computer vision, drone simulation, and field-level automation.

- ### Stage 1: Aruco Marker Detection

  Using **OpenCV**, we detected Aruco markers placed on strawberry boxes. From the camera feed, we extracted:
  - Marker ID
  - 2D orientation
  - Relative position from the camera

  This enabled the drone to identify and align with the boxes.

- ### Stage 2: Drone Flight Control (Gazebo Simulation)

  With the **PX4 autopilot** and **MAVROS**, we simulated where the drone could:
  - Take off,
  - Fly through predefined waypoints, and
  - Land safely.
  
  Basic autonomous navigation was achieved in a 3D Gazebo environment.

- ### Stage 3: Integrated Box Detection and Pickup

  A single strawberry box with an Aruco marker was placed in the drone’s path. The implemented logic was:
  - The drone scans during flight.
  - Upon detecting a box, it hovers, aligns, and lands precisely over it.
  - The **gripper module** is activated to pick the box.
  - The drone ascends and proceeds to the final target location.

- ### Stage 4: Full Field Automation

  A field-like layout was created with:
  - Rows of strawberry plants,
  - Randomly placed strawberry boxes in between the rows,
  - Two **color-coded trucks** as drop zones are placed on the sides of the field.

  #### Mission Plan:
  1. Drone takes off and stabilizes at 10m altitude.
  2. Executes a **row-wise search** to scan for boxes.
  3. On detecting a box:
     - Aligns iteratively and lands on the box.
     - Picks up the box using the gripper.
     - Classifies box color and flies to the corresponding truck.
     - Lands and places the box in a **grid pattern** on the truck bed.
  4. Resumes the search from the last position.
  5. Repeats until the entire field is cleared.

---

## 3. My Role

- Implemented **Aruco marker detection** and vision-based alignment
- Integrated detection with **PX4 drone control**
- Developed the **centering and descent logic**
- Tested **field simulations** in Gazebo

---

## 4. Tools Used

| Tool            | Purpose                                |
|-----------------|----------------------------------------|
| **Python**      | Scripting control logic                |
| **OpenCV**      | Computer vision and marker detection   |
| **ROS**         | Middleware for robotics communication  |
| **MAVROS**      | MAVLink-ROS interface                  |
| **PX4 Autopilot** | Firmware for drone control          |
| **Gazebo**      | Drone and environment simulation       |



---

## 5. Results / Conclusion / Future Scope

- Successfully simulated a drone that autonomously:
  - Scans a field,
  - Detects and collects strawberry boxes,
  - Classifies them by color, and
  - Drops them accurately in designated trucks.

  ### Future Enhancements:
  - Extend to **multi-drone coordination** for faster coverage
  - Integrate **optimized path planning** and collision avoidance
  - Transition from simulation to **real-world implementation**

This project highlights how robotics and automation can significantly impact **agricultural logistics**, pushing forward the vision of **smart farming**.

---
