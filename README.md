# Autonomous-Drone

1. Project Overview
This repository documents the design, development, and fabrication of an autonomous unmanned aerial vehicle (UAV). The primary mission is to perform a fully autonomous payload delivery task:
Takeoff & Pickup: Start from a home position and pick up a 200g payload.
Navigation: Ascend to a stable altitude of 10 meters.
Transit: Navigate 300 meters forward to a pre-defined GPS coordinate.
Delivery: Accurately drop the payload onto a bullseye target.
The drone is engineered for both manual control via a radio transmitter (using ELRS) and fully autonomous operation using the Pixhawk flight controller and a Jetson Nano companion computer.


2. System Architecture & Components
The drone is built using a carefully selected set of high-performance components to ensure reliability and performance.
Flight Control & Avionics:
Flight Controller: Pixhawk 2.4.8
Positioning: GPS Module
Propulsion System:
Motors: Xing BLDC Motors
ESC: T-Motor 4-in-1 ESC
Propellers: 9-inch Carbon Fiber Props
Main Power System:
Battery: 6S 4000mAh LiPo Battery
Autonomous & Vision System:
Companion Computer: NVIDIA Jetson Nano
Camera: Raspberry Pi HQ Camera
Control & Telemetry:
RC Link: ELRS Receiver
FPV: DJI FPV Camera
Payload Mechanism:
Actuator: Servo Motor for pickup and drop mechanism


3. My Contribution: Regulated Redundant Power Supply (RPS)
My core responsibility was the design and fabrication of a critical safety subsystem: a Regulated Redundant Power Supply (RPS) for the flight controller and companion computer.
Problem Statement
A failure of the main 6S flight battery or its power distribution system is a catastrophic single point of failure. This would result in an immediate loss of power to the Pixhawk flight controller and the Jetson Nano, leading to a complete loss of the aircraft.
Solution: The RPS
To mitigate this risk, I developed an independent power module that ensures the drone's "brain" remains active even if the main power fails. This provides a crucial window for a controlled descent, data logging, or recovery.
Key Features of the RPS:
Power Redundancy: The RPS is built around a secondary 2S LiPo battery, which automatically provides power to the flight controller if the main 6S battery voltage drops or is disconnected.
Battery Protection: An integrated 2S Battery Management System (BMS) protects the backup LiPo from over-charge, over-discharge, and short-circuits, ensuring its health and readiness.
Stable Power for Companion Computer: The module includes an onboard 5V step-down (buck) converter that supplies clean, regulated power directly to the Jetson Nano. This isolates the sensitive computer from potential voltage spikes or sags from the main power system, preventing data corruption or reboots during flight.
This RPS design significantly enhances the drone's reliability and resilience, protecting valuable onboard components and mission-critical data.
