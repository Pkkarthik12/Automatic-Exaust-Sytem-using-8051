# Automatic Exhaust System Using 8051 Microcontroller
 
An embedded systems project that automatically activates an exhaust ventilation system when harmful gas levels are detected, using the 8051 microcontroller as the control unit.
 
---
 
## Project Overview
 
This project implements an **automatic exhaust control system** that continuously monitors the surrounding air quality using a gas sensor. When the sensor detects gas concentration above a safe threshold, the 8051 microcontroller triggers a relay to turn ON the exhaust fan/motor automatically — without any manual intervention. Once the air quality returns to a safe level, the system turns the exhaust OFF.
 
This kind of system is practical in kitchens, laboratories, garages, and industrial environments where gas leaks or poor ventilation pose a safety risk.
 
---
 
## How It Works
 
1. The **gas sensor** continuously monitors air quality and outputs an analog/digital signal based on gas concentration
2. The **8051 microcontroller** reads the sensor output and compares it against a preset threshold
3. If gas is detected above the threshold, the microcontroller sends a HIGH signal to the **relay driver circuit**
4. The **relay** switches ON, completing the circuit to the **exhaust motor/fan**
5. The exhaust fan runs until gas levels drop back to safe levels, at which point the relay switches OFF automatically
---
 
## Components Used
 
| Component | Description |
|---|---|
| AT89C51 (8051) | Main microcontroller — reads sensor, controls relay |
| Gas Sensor (MQ-2/MQ-6) | Detects LPG, smoke, CO, and other gases |
| Relay Module | Electrically isolates and switches the motor circuit |
| DC Motor / Exhaust Fan | The actuator — activated when gas is detected |
| Transistor (BC547) | Relay driver to amplify microcontroller output signal |
| Diode (1N4007) | Flyback protection across the relay coil |
| Resistors & Capacitors | Supporting passive components for signal conditioning |
| Power Supply (5V / 12V) | Powers the microcontroller and motor separately |
| Crystal Oscillator (11.0592 MHz) | Clock source for the 8051 |
 
---
 
## Circuit Description
 
- The gas sensor output is connected to one of the digital input pins of the 8051 (e.g., P1.0)
- The relay control signal is driven from an output pin (e.g., P2.0) through a transistor (BC547) acting as a switch
- A flyback diode is placed across the relay coil to suppress voltage spikes when the relay de-energizes
- The exhaust motor is connected to the relay's NO (Normally Open) contacts
- The 8051 is clocked with an 11.0592 MHz crystal and reset circuit (10µF capacitor + 10kΩ resistor)
---
 
## Proteus Simulation
 
The complete circuit has been designed and simulated in **Proteus Design Suite**.
 
📁 Simulation file: [`simulation/automatic_exhaust_system.pdsprj`](simulation/automatic_exhaust_system.pdsprj)
 
> Open the `.pdsprj` file in Proteus 8 or later to run the simulation. Make sure the HEX file is loaded into the AT89C51 component before running.
 
### Simulation Preview
 
![Proteus Simulation](images/proteus_simulation.png)
 
---
 
## Project Photo
 
The hardware prototype of the Automatic Exhaust System:
 
![Project Photo](images/project_photo.jpg)
 
---
 
## Folder Structure
 
```
.
|-- README.md
|-- simulation/
|   `-- automatic_exhaust_system.pdsprj   # Proteus simulation file
|-- images/
|   |-- proteus_simulation.png            # Screenshot of Proteus circuit
|   `-- project_photo.jpg                 # Photo of hardware prototype
|-- src/
|   `-- exhaust_system.asm                # 8051 Assembly source code
`-- hex/
    `-- exhaust_system.hex                # Compiled HEX file for microcontroller
```
 
---
 
## Key Concepts (Electronics & Instrumentation)
 
- **Sensor interfacing** — Reading analog/digital output from MQ-series gas sensors with the 8051
- **Relay driving** — Using a transistor as a switch to drive an inductive load safely
- **Threshold detection** — Comparing sensor values in software to trigger actuation
- **Flyback protection** — Diode placement to protect the microcontroller from relay coil spikes
- **Sensor drift** — MQ sensors require a warm-up time (~20 seconds) before stable readings
- **Noise handling** — Debouncing and threshold hysteresis prevent rapid relay switching
---
 
## Applications
 
- Kitchen exhaust automation
- Garage and basement ventilation
- Industrial gas leak response systems
- Laboratory fume hood control
- LPG leak safety systems
---
 
## Author
KARTHIK PK
Electronics and Instrumentation Engineering
[Federal Institute of Science and Technology(FISAT)]
