# Open-Source Hybrid Caged Quadcopter & Ground Crawler

Welcome to the official repository for the **Hybrid Caged Quadcopter-Crawler**. This project provides complete hardware specs, CAD structural layouts, mechanism design, and assembly instructions to build an autonomous hybrid drone equipped with a transforming icosahedral protective cage and a ground-crawling wheel system from scratch.

---

## 🚀 Repository Structure

```text
├── CAD/
│   ├── chassis/              # CNC Milling files (.DXF, .STEP)
│   ├── 3d_printed_parts/     # SLA & SLS 3D models (.STL, .3MF)
│   └── cage/                 # PA12-CF lattice segments (.STEP)
├── Hardware/
│   └── BOM.md                # Interactive Bill of Materials
├── Firmware/
│   ├── betaflight/           # Flight controller target configuration
│   └── servo_actuator/       # Arduino/ESP32 code for cage transformation
└── Docs/
    ├── Assembly_Guide.md     # Step-by-step assembly manual
    └── Wiring_Diagram.pdf    # Complete electrical pinout
```

---

## 🛠️ Complete Technical Specifications

### 1. Core Frame & Avionics Enclosure
* **Main Lower Chassis Plate:** 2.5 mm 3K Matte Carbon Fiber Sheet (CNC-milled) with standard 30.5 x 30.5 mm stack mounting pattern and integrated battery strap slots.
* **Upper Deck & Canopy:** SLA-printed PETG housing providing thermal isolation for internal stack components and rigid mounts for the stereo FPV camera array.
* **Arm Geometry:** True-X configuration built with 4 mm chamfered carbon fiber arms designed to absorb high radial impact forces.

### 2. Protective Geodesic Cage Assembly
* **Lattice Structure:** Flexible icosahedral carbon-fiber reinforced nylon (PA12-CF) cage with 3.0 mm uniform wall thickness.
* **Articulation Joints:** Dual-sided TPU flexible hinges (95A durometer) mounted at four equatorial pivot points, allowing complete hemispherical expansion into crawling mode.
* **Quick-Release Clamps:** Stainless steel M2 quick-release pin mounts securing the cage to outer motor bases for fast field maintenance.

### 3. Actuation & Mechanism Parts
* **Drive Gearbox:** Precision SLS Nylon-12 double-reduction stage:
  * **Worm Gear Stage:** Brass worm gear (0.5 module) driving a 30-tooth steel gear for zero-backlash, non-reversible high-torque locking.
  * **Toothed Sector Gear:** 1.0 module spur gear segment connected directly to the upper wheel arm linkage.
* **Suspension & Damping:**
  * **Piston Rod & Cylinder:** SLA Resin housing with an integrated oil-filled micro shock absorber.
  * **Coil Spring:** Linear steel spring (0.8 mm wire diameter) located inside the lower thigh member.
  * **Micro Servos:** Dual high-torque metal-gear micro servos (9g, 2.5 kg·cm) driving the transformation mechanism.

### 4. Drivetrain & Wheel Subsystem
* **Drive Wheels:** 6x custom 3D-printed TPU rim cores wrapped in high-traction ribbed rubber tires (35 mm outer diameter).
* **Wheel Hub Assemblies:** Precision-machined aluminum hex adapters fitted with dual 3 x 6 x 2.5 mm sealed ball bearings per hub.
* **Linkage Arms:** CNC carbon-fiber links connecting the central frame chassis to the articulating wheel carriers.

### 5. Hardware & Fasteners
* **Fasteners:** Anodized 7075 Aluminum M3 socket head cap screws for structural frame connections; M2 button head screws for precision gear enclosure mounting.
* **Standoffs:** Hexagonal knurled aluminum standoffs (30 mm, M3 threaded).
* **Inserts:** Heat-set brass inserts (M2 and M3) embedded in all 3D-printed structural housings.

---

## 📦 Bill of Materials (BOM) & Sourcing

| Component | Material / Model | Qty | Fabrication Method |
| :--- | :--- | :--- | :--- |
| **Chassis Base** | 3K Carbon Fiber (2.5 mm) | 1 | CNC Router |
| **Frame Arms** | 3K Carbon Fiber (4.0 mm) | 4 | CNC Router |
| **Geodesic Lattice** | PA12-CF Nylon | 1 | SLS Printing |
| **Flexible Hinges** | TPU 95A | 8 | FDM Printing |
| **Gear Set** | Steel / Brass / Nylon-12 | 1 Set | Machined / SLS |
| **Dampener Cylinders** | Tough SLA Resin | 4 | SLA Resin Printing |
| **Wheel Rims** | TPU 95A | 6 | FDM Printing |
| **Wheel Tires** | Soft Rubber Compound | 6 | Injection Molded / Cast |
| **Ball Bearings** | 3 x 6 x 2.5 mm Sealed Steel | 12 | Off-the-shelf |
| **Fastener Kit** | 7075 Aluminum M2/M3 Screws | 1 Set | Off-the-shelf |

---

## ⚙️ Assembly Instructions Overview

1. **Frame Stack Construction:** Insert M3 heat-set brass inserts into the upper canopy. Bolt the four 4 mm carbon fiber arms between the lower chassis plate and mid-deck using aluminum standoffs.
2. **Gearbox Integration:** Press fit the brass worm gear onto the micro servo output shaft. Align the 30-tooth steel gear inside the gearbox housing, securing it with M2 button head screws.
3. **Suspension Linkage Assembly:** Slide the linear coil spring and piston rod into the SLA-printed cylinder. Secure the assembly to the carbon linkage arm using M2 pins.
4. **Wheel & Hub Mounting:** Press dual 3 x 6 x 2.5 mm bearings into each wheel rim. Mount the wheel hub assemblies to the articulating arms via aluminum hex adapters.
5. **Cage Mounting & Wiring:** Connect the PA12-CF cage segments using the 95A TPU hinges. Mount the full assembly onto the frame using the quick-release stainless steel pin mounts. Route servo wires directly to the auxiliary outputs on your flight controller.

---

## 💻 Firmware Setup

1. **Flight Controller Setup:** Flash Betaflight or ArduPilot target configuration located in `/firmware/betaflight/config.cli`.
2. **Servo Output Allocation:** Map Aux Channels 1 & 2 to trigger the dual transformation servos:
   * **PWM 1000us:** Flight / Rolling Mode (Fully Enclosed Cage)
   * **PWM 2000us:** Crawling Mode (Expanded Cage, Exposed Wheels)
3. **Calibrate Gear Lock:** Adjust endpoint values to ensure the worm gear fully locks the sector gear without stalling the micro servos.

---

## 📜 License

Distributed under the **CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S)**. See `LICENSE` for details.
